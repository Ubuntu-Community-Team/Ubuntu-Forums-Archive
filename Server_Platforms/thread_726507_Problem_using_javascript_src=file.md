---
title: "Problem using javascript src=file"
date: 2008-03-16
forum: Server Platforms
---

### Post by wgw on 2008-03-16
I have just set up a dapper server. I have a helloworld.js and helloworld.htm files in public_html . Permissions are set on both as: 755. The onclick function in the .htm file does not work (error message:  helloworld not defined); I assume the .js is not getting read into the html page. This is weird. It should work; any ideas? (I'm imagining that the server is configured to block reading .js files...)

Thanks!


helloworld.htm:

  [INDENT]  <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
    <HTML>
    <HEAD>
<meta http-equiv="content-type" content="text/html; charset=iso-8859-1"
<script type="javascript/text" src="helloworld.js"> 
</head>
<body>
<button onclick="helloworld();"> Click </button>
</body> </html>
[/INDENT]
helloworld.js:

[INDENT]function helloworld(){ 

alert("hello world");
} [/INDENT]

---

