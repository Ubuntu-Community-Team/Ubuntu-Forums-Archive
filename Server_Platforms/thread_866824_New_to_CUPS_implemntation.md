---
title: "New to CUPS implemntation"
date: 2008-07-22
forum: Server Platforms
---

### Post by accessbalaji on 2008-07-22
[B]Guys,
	I am new to CUPS and i have read only few introduction documents on CUPS and IPP. [/B]I have a problem here. I have a business requirement here. We are going to host a new 
	website. In that we have requirement , the client who are accessing the website will have the local network 
	printers attached to them. In one of the page , they will say print. When they o it, i must find the printer
	which is attached to them and print the data.
	
	Is this possible with the help of CUPS. If yes, how do i install cups . Should i have seperate machine as a 
	print server ? Is there any books or documents which gives a complete installation and configuration steps for CUPS.
	And also give me steps to implement the above scenario. 
	
	**Please somebody help me. :)**

---

### Post by AndyCee on 2008-07-22
While someone more knowledgeable should turn up soon...
...CUPS will not be enough to do what you want. I use CUPS as a print server at home. Setting up & installing a CUPS server is easy (I'll be more specific if you can give a bit more information). You probably should have a seperate print server, just for scalability & stability reasons.

The tricky bit (or at least, where my knowledge crumbles) is getting the host web page to send a print job to CUPS.

Just to clarify:


[LIST]
[*] Your website is hosted locally, and clients can access your website from the internet?
[*] Your web site is hosted on Ubuntu-desktop? Ubuntu-server? Something else?
[*] Is the data the client will print inside a program or on a web page?
[/LIST]

I am very ignorant of web technology, but if you can clarify these questions I'm sure it will help with a response.

---

### Post by accessbalaji on 2008-07-22
**First of all thanks AndyCee.**

Your questions were 

**1) Your website is hosted locally, and clients can access your website from the internet? **

            My website is hosted locally. Actually its a web application that we are creating.

**2) Your web site is hosted on Ubuntu-desktop? Ubuntu-server? Something else? .**

         My application will be running in a weblogic server.

**3) Is the data the client will print inside a program or on a web page?**

         The data will print inside a program. 

  And can you provide me any document which has a step by step procedure to install CUPS.

---

### Post by AndyCee on 2008-07-22
Before I proceed I must mention I am a home user with some very limited enterprise experience. I've never touched a weblogic server before.

I have a few links which might help. In order to provide a step-by-step procedure to install CUPS, you need to know on what operating system, as the installation procedure will vary between different OS's. CUPS is an application/package, so requires installation on an OS.

On Ubuntu-desktop, it is already installed. There is a simple GUI under
System -> Administration -> Printing

An OLD document which will answer many questions about CUPS is here (includes features of CUPS - some of which would be upgraded by now):
[http://www.nluug.nl/events/sane2002/papers/SANE2002_3.pdf](http://www.nluug.nl/events/sane2002/papers/SANE2002_3.pdf)

This site has all the backend explanations for CUPS-IPP, which is generic to OS and also beyond my understanding:
[http://www.cups.org/documentation.php/spec-ipp.html](http://www.cups.org/documentation.php/spec-ipp.html)

This site has a howto for Ubuntu network printing, including IPP:
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

There are obviously network considerations (ports, UAC, server load, possibly SAMBA) which I can't help with.

That's all I have at the moment. Ask more if you think of anything.

-Andrew

---

### Post by accessbalaji on 2008-07-23
Thank you for a detail explanation. 
Can we install CUPS in windows OS. Where can i find the installer. Because  whereever i see in the internet, it has installer related to Linux or Unix.

---

### Post by ad_267 on 2008-07-23
CUPS is an acronym for Common Unix Printing System, so no I don't think you can install it on a Windows server. I don't know what the equivalent software for Windows would be.

---

### Post by accessbalaji on 2008-07-23
Thank you :). So can you suggest me a Linux version OS or some OS where i can install CUPS or some OS which you have tried with so that you can help me more on this. What should be my minimum configurations of my machine to have CUPS installed on it.

---

### Post by ad_267 on 2008-07-23
Any linux OS should be able to run cups. If you're happy using only the command line you could try ubuntu server edition or if you would like a gui you can use the ubuntu desktop edition or install the server edition then install the ubuntu-desktop package.

Ubuntu comes with CUPS already, and you don't need a powerful computer just to run a server.

---

### Post by accessbalaji on 2008-07-23
Thank you .Do i need Ubuntu server and the Ubuntu client also. From where can i download Ubuntu server edition . Is it a freeware.

---

### Post by ad_267 on 2008-07-23
Ubuntu is free software. Ubuntu server is just specialised for servers and comes with different packages and it has no graphical interface by default.

You probably just want to stick with the desktop edition as that will be easiest to set up.

You can download Ubuntu here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by accessbalaji on 2008-07-23
My target server is a Red Hat Linux 4.0. Can i use this ubuntu software desktop edition and install it in Red Hat Linux.

---

### Post by ad_267 on 2008-07-23
You can install CUPS on red hat. It should be installed already.

Ubuntu is a whole Linux based operating system, just like Red Hat.

---

### Post by AndyCee on 2008-07-23
This has exactly your question. Try typing the commands in the last post into terminal.

[http://www.linuxquestions.org/questions/red-hat-31/starting-cups-in-rhel-420654/](http://www.linuxquestions.org/questions/red-hat-31/starting-cups-in-rhel-420654/)

---

### Post by accessbalaji on 2008-07-23
Thank you guys. Yes ad_267 in my RedHat , the CUPS is already there. I need to configure that alone i think ? :)

Thanks AndyCee. That document was good. Ill try to configuremy server with the help of the documents. 
Ill get back to both of you if have more road blocks.

Thanks

---

### Post by AndyCee on 2008-07-23
Let us know how you go when it's set up. Most of these threads have questions or problems, so it's nice to hear about a working solutions at the end.

---

