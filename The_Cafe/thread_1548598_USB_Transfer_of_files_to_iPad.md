---
title: "USB Transfer of files to iPad"
date: 2010-08-08
forum: The Cafe
---

### Post by Jimleko211 on 2010-08-08
I was wondering if on Linux, there is a way to transfer files to the root of the iPad (it is jailbroken), much like you can on mac and windows using iPhone Explorer.

---

### Post by tilapia on 2010-08-08
You can probably do this if you enable SSH. You should then be able to use 'Places' > 'Connect to Server' and enter the SSH details.

---

### Post by forrestcupp on 2010-08-08
I thought iPads didn't have USB capability.

---

### Post by Jimleko211 on 2010-08-08
@Forrestcupp: They're not supposed to.  But you can if you use a program that allows it, such as iPhoneExplorer.  You can then get into the root if you've jailbroken it.

I have solved my issue, by using a program named scp.  It uses SSH as the base, I think, and it's a command line app, but it does its job well.

---

### Post by forrestcupp on 2010-08-08
> **Jimleko211 said:**
> @Forrestcupp: They're not supposed to.  But you can if you use a program that allows it, such as iPhoneExplorer.  You can then get into the root if you've jailbroken it.

So it has a USB port?

---

### Post by Sand &amp; Mercury on 2010-08-08
> **forrestcupp said:**
> So it has a USB port?
It can connect to a PC via USB but doesn't have any ports of its own (like the iPhone). You can transfer stuff to/from it, but you can't stick in a flash drive etc.

---

### Post by Jimleko211 on 2010-08-08
> **Sand & Mercury said:**
> It can connect to a PC via USB but doesn't have any ports of its own (like the iPhone). You can transfer stuff to/from it, but you can't stick in a flash drive etc.
Exactly, that's what I mean.  I mean plugging my iPad into the computer and then transferring files.

---

### Post by an0dos on 2010-08-20
> **Jimleko211 said:**
> Exactly, that's what I mean.  I mean plugging my iPad into the computer and then transferring files.

You can transfer files from a USB stick if it is jail broken and you have the camera connection kit. I believe the ifile app from the cydia store will work for that. Ifile also has a server function that will allow you to browse the file system on the iPad from a remote system using the remote system's web browser. Ifile also has a text editor and other useful features. Definitely worth checking into on a jail broken iPad. With a little work and some ingenuity you can use a jailbroken iPad as a laptop replacement.

---

### Post by abhi.datt on 2010-09-30
Just install this AMAZING!! application called Goodreader from App store and you are sorted. (It is cheap even at 10 times its price, just proced at $ 0.99) 
Not only it's an excellent document (PDF,DOC.etc) reader it provides the simplest way to connect to your iPAD by converting it into a WebDAV server instantaneously (over the WiFi).No USB required at all. 

**iPAD**
On your iPAD click on the Goodreader icon > Connect to Servers > Click on the Wireless icon on the bottom panel 
This will provide you the connect URL and port for your iPAD
For instance, in my case ([http://192.168.1.2:8080](http://192.168.1.2:8080)) 

**Ubuntu**
You can then goto Ubuntu > Places > Connect to Server...  > WebDAV (HTTP) and give the IP Address and port that you get for above step.

That's all. Create new folders, put your PDFs, docs even video files.

I found this application extremely useful since I need not to go to Windows to transfer/manage files/folders nor I need to carry my USB stuff always. 

I guess it can even handle images, but I need to still test that.

---

### Post by jfreak_ on 2011-09-05
Talk about bringing stuff back to life....

---

### Post by mikesalguero on 2011-09-10
I am new to this forum, and to ubuntu so apologize if any questions I have are dumb!   
 I downloaded this app, and connected just fine. 
I  am trying to upload multiple folders at once; Goodreader doesnt have good documentation for ubuntu (10); 
Got this error when I went to Places--Network--Ipad:  

Error resolving "_webdav._tcp" service "Michael  Salguero’s iPad" on domain "local". One or more TXT records are missing. Keys required: "u".


any thoughts?


> **abhi.datt said:**
> Just install this AMAZING!! application called Goodreader from App store and you are sorted. (It is cheap even at 10 times its price, just proced at $ 0.99) 
Not only it's an excellent document (PDF,DOC.etc) reader it provides the simplest way to connect to your iPAD by converting it into a WebDAV server instantaneously (over the WiFi).No USB required at all. 

**iPAD**
On your iPAD click on the Goodreader icon > Connect to Servers > Click on the Wireless icon on the bottom panel 
This will provide you the connect URL and port for your iPAD
For instance, in my case ([http://192.168.1.2:8080](http://192.168.1.2:8080)) 

**Ubuntu**
You can then goto Ubuntu > Places > Connect to Server...  > WebDAV (HTTP) and give the IP Address and port that you get for above step.

That's all. Create new folders, put your PDFs, docs even video files.

I found this application extremely useful since I need not to go to Windows to transfer/manage files/folders nor I need to carry my USB stuff always. 

I guess it can even handle images, but I need to still test that.

---

### Post by Thalarse on 2011-11-07
Sorry to re-ressurect this thread, but i have the use of an ipad for a few weeks, and was hoping to add a few pdf files to it for my studies (and also copy the course notes onto my computer for later referal). I can connect the ipad to my netbook and it mounts on its own without any fuss, however i can't find the folder containing the pdfs. 

The program on the ipad is called PDFReader Pro. My netbook is running 10.04 vanilla. 

I tried looking at hidden folders (there aren't any), and still can't find the files. Am i missing something? I really wish the training company had bought galaxy tabs instead! haha 


Anyway thanks for any advice.

*edit* 

Never mind, it turns out that PDFReader Pro has a http server feature, which is pretty neat. Thanks anyway.

---

### Post by mage7 on 2011-12-29
Also, Calibre (downloadable from the Software center) supports transfer of books to iPad/iPhone over Wi-Fi through a similar http server mechanism.

ps: Sorry for re-re-resurrecting this thread, but i stumbled upon it while googling the same question, and i thought that this info might be helpful to others.

---

### Post by Uffish on 2012-04-21
From the menu choose File > Connect to server. Put type = Webdav, Server = 10.0.0.3 or what the ipad tells you, port = 8080. Click connect. Worked for me.

---

