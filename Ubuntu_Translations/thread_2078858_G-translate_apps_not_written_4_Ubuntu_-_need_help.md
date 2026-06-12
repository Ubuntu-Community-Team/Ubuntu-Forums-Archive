---
title: "G-translate apps not written 4 Ubuntu - need help"
date: 2012-10-31
forum: Ubuntu Translations
---

### Post by Ace..... on 2012-10-31
I'm creating a translation tool that will be very useful for our community, because google is not writing its apps for us.
We don't need them, cos I've figured a concept that can give us what we need..... and better than what google offers. 

The concept is: source text --> translation --> source language.
Effectively this is Nirvana.

The ability to write as you will, and see how google translate brings your translated document back to (say) english is the ultimate requirement.

The standard translation, is almost there, but not quite.
If you don't understand the intricate detail of the foreign language (you are translating your text into)... then you will end up with sad, and possibly ridiculous errors.

By re-translating the the translation back to English, you will be 100% certain that the translation was perfect.

Okay.... that's the concept (we can do it now but it's pathetic - see below).

Unless you are an ace in all languages, I guess this will be extremely useful to you.

[SIZE="2"]**How To Do It?**[/SIZE]

With the simple tools that google gives ubuntu users, I believe we can create this tool 

Primarily the current design is a web page containing 3 iframes, split 33% of the screen, displaying page1, page2, page3.

The objective is to type or paste your source text into page1.

By clicking on page1, this would transfer the text to page2, where google translate will translate it to a language of your choice.

Ideally, this translated text should auto-appear in page3, and be translated back to english (but a mouse click would suffice for starters).

[SIZE="2"]**Where am I up to?**[/SIZE]
I'm experimenting with textarea variables.

I'm struggling to pass a local variable (in function textarea variable) to a global variable, to allow page2 to display what was typed in page1.

If we could get page2 to display what has been typed in page1 (and thereby be translated), then we could surely pass page2 translated text to page3, where it would be translated back to english.

This is my code contained in my javascript doc:

```
var textt="initial variable";

function iframe_variables(){
textt = document.getElementById("styled").value;
}

function iframe(){
iframe_variables();
document.write('<div>');
document.write('<HR><P><B>', (textt), '</B><BR>');
document.write((textt), '</P>');
document.write('</div>');
}

function iframe2(){

document.write('<div>');
document.write('<HR><P><B>', (textt), '</B><BR>');
document.write((textt), '<BR>');
document.write('</div>');
}
```
This is the code in page1:

```
<body  OnLoad="document.myform.styled.focus();">
<div id="container1">
<form name="myform">
<textarea  name="styled" id="styled" onclick="iframe()">
</textarea>
<br><br>
</form>
```
The above allows me to type the text, and when 
I'm ready, I'll click on the text, to pass the variable.

This is the code in page2:

```
<input type="text" name="txt0" id="txt2" value="" onclick="iframe2()">
```
[SIZE="2"]**The problem is:**[/SIZE]
In page1 I get what I type.
In page2 I get the initial variable.

I don't know how to transfer the local variable to global variable, accessible by all pages on the site.

**[SIZE="2"]Other nice jobs[/SIZE]**
There will be a need to insert a line break on 'enter' (while writing or pasting the text into page1 textarea.

This will make the text more readable.

If that can be achieved, I would place page3 next to page1, so that the final reverse translation can be quickly compared to the original.

Page2 would be the text that is finally transferred to the web site, without any fear of stupid errors.

[SIZE="2"]**Can you do this now?**[/SIZE]

You can do this..... but it's painful.
You must load 2 tabs with google translate, and copy the translated output to the 2nd tab source, which produces the reverse translation.

For every single change you make, you must repeat this.
It totally kills creativity.

Anyway.... can anybody help?
__________________

---

### Post by Ace..... on 2012-11-01
Well it looks as though the way to do this is with html5 localstorage.

I've got page 2 displaying the text written into page 1. :P

I've fixed the line break problem, for page2 display by using <pre> tags. :P

I now just need to get page3 to display 'page2 text'.

It's going well.

---

### Post by Ace..... on 2012-11-01
Managed to get page3 working. :P

First I store the **page1** textarea contents using onclick to launch this function:

```
function store_pg_1()
  {
var pg_1 = document.getElementById("textarea_id").value;
  localStorage.pg_1_text=pg_1;
  }
</script>
```

**On page2** I now access 'localStorage.pg_1_text' and write it to page:

```
<div id="result">
<script>
if(typeof(Storage)!=="undefined")
  {
  document.getElementById("result").innerHTML="<pre>" + localStorage.pg_1_text + "</pre>";
  }
else
  {
  document.getElementById("result").innerHTML="Sorry, your browser does not support web storage...";
  }
</script>
```

Notice the use of <pre> to ensure line breaks are maintained.

To store the page2 text (after translation we hope), this script is placed in the head (onclick trigger):

```
function store_pg_2()
  {
pg_2 = document.getElementById("result").innerHTML
  localStorage.pg_2_text=pg_2;
  }
</script>
```

**On page3** I now access 'localStorage.pg_2_text' and write it to page:

```
<div id="result">
<script>
if(typeof(Storage)!=="undefined")
  {

  document.getElementById("result").innerHTML="<pre>" + localStorage.pg_2_text + "</pre>";
  }
else
  {
  document.getElementById("result").innerHTML="Sorry, your browser does not support web storage...";
  }
</script>
</div>

```

So what I write in page1, appears in page2, and page2 appears in page3.

Just need to find out how the translated text appears in page2.

---

