---
title: "HTML5 + JS project - Editor"
date: 2011-06-29
forum: Utah Team - US
---

### Post by slooksterpsv on 2011-06-29
So I'm making an editor in HTML5 and Javascript. I know there are others out there, but I wanted to try and make on, using the Canvas object. So I wanted to share the code and that with everyone here and I'm stating this right now, it's licensed under the GPLv2, not v3, I want it under v2 and to stay under v2.

Here's the code
```

<html>
<head>
<title>Canvas</title>
</head>
<body>
<canvas id="editor" width="500" height="350" style="border:1px solid #000000; positoin:absolute;">
</canvas>
<br/>
<textarea id="code" onKeyPress="javascript:writeInCanvas(document.getElementById('code').value);"></textarea>
<script language="javascript">
var canvas = document.getElementById('editor');
var ctx = canvas.getContext('2d');
var ce_focused = false;
var buffer = "";

//For the cursor
var cursorX = 1;
var cursorY = 0;
//for letter positioning of the cursor
var letPosX = 0;
var letPosY = 0;

function init() {
 //Initialize event listener for typing on the canvas.
 window.addEventListener('keypress', ce_typing, false);
 canvas.addEventListener('click', ce_focus, false);
}

function ce_focus(ev)
{
 //Tell whether or not we've clicked in the editor
 //and want to start typing
 if((ev.layerX <= 500) && (ev.layerY <= 350))
 {
  ce_focused = true;
 }
 else
 {
  ce_focused = false;
 }
}

function ce_typing(ev)
{
 //If we're clicked in the editor and start typing type
 if (ce_focused)
 {
  //Prevent default actions
  ev.preventDefault();
  var evtobj=window.event? event : ev; //distinguish between IE's explicit event object (window.event) and Firefox's implicit.
  var unicode=evtobj.charCode? evtobj.charCode : evtobj.keyCode;
  var actualkey=String.fromCharCode(unicode);
  if (unicode == 8)
  {
   //test for backspace
   //location and positioning determined by a cursor will follow
   buffer = buffer.substring(0, buffer.length-1);
  }else if (unicode == 13) {
   buffer += "\n";
  }else if (unicode == 39) {
   buffer += "'";
  }
  else {
   buffer += actualkey;
  }
  writeInCanvas(buffer);
 }
}

function showCursor(x,y)
{
 ctx.fillStyle = "black";
 ctx.fillRect(x,y,5,11);
 //document.write(x + " " + y);
}

function writeInCanvas(text)
{
 //Clear the canvas, fill it blue, set font and put text in it. 
 ctx.clearRect(0,0,500,350);
 ctx.fillStyle = "blue";
 ctx.font="10pt Helvetica";
 if (text.match('\n'))
 {
  //Split the text and find all locations of \n
  var array = text.split("\n");
  for(var y=1; y <= array.length; y++)
  {
   //iterate through and fill the text on the screen
   ctx.fillText(array[y-1], 5, 10*y+1);
   cursorY = y-1;
   cursorX = Math.round(ctx.measureText(array[y-1]).width);
  }
 }
 else
 {
  //if not \n's just add text
  ctx.fillText(text, 5, 11);
  cursorX = Math.round(ctx.measureText(text).width);
 }
 showCursor(cursorX+6,cursorY*10+1);
}

init();
</script>
</body>
</html>

```

What do you think?

---

