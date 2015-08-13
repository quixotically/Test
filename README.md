# Thinking About Games: Essay Form

## Technologies
I used Formspree to send emails without a backend, and CKEditor to add  word-processing features to the textarea. CKEditor is an amazing tool that is very customizable - check it out! The biggest downside is that the API documentation is not very good. I added the AutoSave and WordCount plugins and removed a few of the included plugins of the full preset to make the customized editor you see in this project.

## TODO
presence verification
change value of button to Submit
- build email title string
- add wordcountreached! popup when wordcount === 300
- check if autosave works in production site

## Questions/Decisions
Caching
replyto

## Features

## Configuring the WordCount plugin
I went into the ckeditor.js file and set maxWordCount to 300 and hardLimit to false to prevent the editor from preventing you to type more than 300 words (if you did this using the minified version, change the 0 to a 1).

Since I could not find a way to get the paragraph count in the API documentation or plugin documentation, I had to manually do this in a script. There is at least a way to get the html content of the replaced textarea, which is ```<editor instance>.getData()```. With this, I just wrapped the string in a div in order to use ```find()```. The result looks like this:
```
$('<div>' + essayHTML + '</div>').find("p").length
```

## Using a downloaded font
1. Download the font you want into your project
2. Convert the ttf file to eof in order for your font to be compatible with IE and insert that into the same folder as the original. This is a free tool to do that: https://www.kirsle.net/wizards/ttf2eot.cgi
3. Insert this CSS at the top
```
@font-face {
 font-family: anyname;
 src: url("path/file.eot");
}
@font-face {
 font-family: anyname;
 src: url("path/file.ttf");
}
```
4. Set ``` font-family: "anyname" ``` on the desired elements!
