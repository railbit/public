## ephemeris

### Instructions

You are already feeling this change in yourself... You can now understand why people say that developers are lazy. You want to do more, but doing less. That's normal.
Let's try to enhance your own routine, as a starter. Every morning you do the same researches to stay aware and prepared for your new day. We're gonna save this precious time.
To do so, we're going to create a script that automate this researches by simulate it in a browser, get the informations you want, and display it all gathered in the console.

> We are talking here about your own interests. This can be found only in youself. What's relevant to you to begin a new day? It is very personnal, be creative!
> Some examples we could see in other people minds: get the weather, the last podcast/article of a media that you like, the last post of a someone/something you follow, your horoscope, the tv program of the day, etc.

About the browser control, you must:
- handle the opening and the closure of the browser
- navigate to a specific url
- click on an element which implies an event in the page (display something, registrer to something, like something...)
- navigate in a website
- get the text content of an element
- get the url of an element

In the end:
- The whole browser control must execute itself without being seen.
- Your ephemeris must appear in your console.
- The script has to finish and close properly.

#### Using puppeteer

In order to get your daily informations out of your favorite websites, you'll have to use `puppeteer` API.

First, create a new repository named `ephemeris` and run this command line in your terminal, in the repository:
```console
student@ubuntu:~/[[ROOT]]/ephemeris$ npm install puppeteer
```

Then, create a new file `ephemeris.mjs` in which you will use the puppeteer module:
```js
import puppeteer from 'puppeteer'

const browser = await puppeteer.launch({
  headless: false, // to be commented or removed when project is submitted
  devtools: true, // to be commented or removed when project is submitted
})
const [page] = await browser.pages()
await page.goto('https://www.google.com/')
// other actions...
await browser.close() // you can comment this during you tests
```

**Puppeteer helper - script model**

```javascript
if ((await page.$('button#myId')) !== null) {
  await page.click('button#myId')
}
await page.waitForSelector('input#myId')
await page.type(`input#myId`, 'myText')
await page.waitForSelector('div#myId')
await Promise.all([
  page.waitForNavigation(),
  page.click('div#myId'),
])
await page.waitForSelector('div#myId')
const myText = await page.$eval(
  'div#myId',
  (s) => s.textContent,
)
```


### Optional

1. Pimp your output. Here are some ideas or examples, be **creative**:
   - Put some colors in your text
   - Associate an emoji to the weather `(< 10°: ❄️; > 10° && < 20°: ☀️; > 20°: 🔥)`
   - Add randoms messages to say hello
   - Etc.

2. Generate a `ephemeris.html` file from this ephemeris
   - Check the first raid! you can use the `style.css` and the `cards` section of the `html` file as an inspiration...

3. Save a file every day in a `/history` folder (with its date) and display the 10 latest files of the history in an HTML page.

4. Integrate your ephemeris in the result of your first `cardon-copy` raid, on the `cards` section.
   - Integration must be dynamic: *each day, your new ephemeris should replace the old one.*

### Notions

- [HTML Elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)
- [HTML Attributes](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes)
- [Puppeteer](https://pptr.dev/)
- [Node process: `exit`](https://nodejs.org/api/process.html#process_process_exit_code)
- [Node file system: `readdir`](https://nodejs.org/api/fs.html#fs_fs_readdir_path_options_callback)
- [Node file system: `readFile`](https://nodejs.org/api/fs.html#fs_fs_readfile_path_options_callback)
- [Node file system: `writeFile`](https://nodejs.org/api/fs.html#fs_fs_writefile_file_data_options_callback)
- [Node path: `resolve`](https://nodejs.org/api/path.html#path_path_resolve_paths)
- [Node utilities: `promisify`](https://nodejs.org/api/util.html#util_util_promisify_original)
- [`getElementById`](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById))
- [`textContent`](https://developer.mozilla.org/en-US/docs/Web/API/Node/textContent)
- [`http-server`](https://www.npmjs.com/package/http-server) or [`serve`](https://www.npmjs.com/package/serve)