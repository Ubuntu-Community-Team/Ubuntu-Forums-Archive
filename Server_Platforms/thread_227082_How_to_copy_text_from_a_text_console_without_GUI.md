---
title: "How to copy text from a text console without GUI"
date: 2006-08-01
forum: Server Platforms
---

### Post by flyingrhino on 2006-08-01
I've got a text only (no X) install of ubuntu server. Sometimes I need to copy and paste text from the screen (to save typing), or simply copy text from the screen and save as a file (in case I have a problem and want to show someone the output).

How do you copy and paste from a text only console ?
There is obviously no mouse to use here.

Thanks.

---

### Post by skizz on 2006-08-01
I think you can copy with CTRL + C and paste with CTRL + V. I'm not sure about this but it should work.

---

### Post by flyingrhino on 2006-08-01
That won't work - you have to somehow mark the section you want first, and there should be some sort of solution to that.
I bet I'm not the first looking for a solution !

---

### Post by xinix on 2006-08-01
If you have a mouse attached to the computer.  It can be used in the console with '*gpm*' (it's in the repos).  Once installed run ```
dpkg-reconfigure gpm
```.  This will run you through some config options.  After this you should have a working mouse in the console.  I'm not familiar with key commands to copy and paste in the console. It might depend on each app. But, if you use the mouse cursor to select the text you want and then press the middle button it'll paste it for you.  I know that if you open a document in nano select the text,  close the document, open a new one and middle click it'll paste what you had selected in the previous doc.

Remember that CTRL + C and CTRL + V have different functions in the console.

Hope this gets you started.

---

### Post by pdc303 on 2006-08-01
Copy: Control+Insert
Paste: Shift+Insert

Control+C does not copy text in a console. Control+C will terminate the active program.

---

### Post by flyingrhino on 2006-08-02
I'm trying that right now. Seems like you guys have got it.

Thanks.

---

### Post by Randomskk on 2006-08-02
An easier option would be to control your server using SSH - this means you get a console for your server on your main pc. It works with windows or linux as your main pc, and then it's incredibly easy to copy text to and from the server.

See this for installation details:
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by flyingrhino on 2006-08-02
I usually do that but sometimes when I am in the network room I can't be bothered to ssh in so I work on the console. This iswhen I run into trouble and the gpm solution works for me.

---

