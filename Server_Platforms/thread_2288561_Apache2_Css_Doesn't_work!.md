---
title: "Apache2: Css Doesn't work!"
date: 2015-07-28
forum: Server Platforms
---

### Post by Alex_Galcik on 2015-07-28
Hi I installed apache2 on Ubuntu 12.04 everything worked fine but css still doesn't work ....Any ideas how to fix it?

---

### Post by slickymaster on 2015-07-28
*Moved to the* **Server Plataforms** *sub-forum*

---

### Post by Lars Noodén on 2015-07-28
How are you doing your Cascading Stylesheets (CSS) in your web pages?  What are the symptoms of them not working?

If they are embedded, they should be served inside the web page itself.  

[html]
...
<head>
  <title>foo</title>
  <style type="text/css" media="screen">
  BODY { font-family: sans-serif; margin: 0; }
  </style>
 ...
</head>
...
[/html]

If they are external, then you just link to them and the browser should be requesting them as needed.  

[html]
...
<head>
  <title>foo</title>
  <link href="somestylesheet.css" rel="stylesheet" type="text/css" media="screen" />
 ...
</head>
...
[/html]

---

### Post by SeijiSensei on 2015-07-28
> **Lars Noodén said:**
> 
If they are external, then you just link to them and the browser should be requesting them as needed.  
[html]
  <link href="somestylesheet.css" rel="stylesheet" type="text/css" media="screen" />
[/html]
And make sure those types of relative links are correct.  That link points to a .css file *in the same directory* as the calling file. That might work in a file at the top of the directory tree like /index.html, but it will fail for files in subdirectories below the DocumentRoot.

I prefer absolute references in most cases for this reason: 
```
href=/somestylesheet.css
```
That points to a file in the root of the web tree.  That link will work regardless of how many levels down in the directory tree the referring file is located.

---

