---
title: "Is FTP my option?"
date: 2007-06-15
forum: The Cafe
---

### Post by Roasted on 2007-06-15
Uh long story short. My gf and I seem to be really into photography. Not like crazy stuff, but we both have digital cameras we take a ton of pictures with, especially her since she got a new cybershot 2 nights ago. Anyway, I find that it's a pain to send the pictures 1 at a time that we seem like we have to show to each other asap.

What are my options with sending bulk pictures? We can't direct connect on aim because I use pidgin (gaim) and it's direct connect feature sucks. Email has a limited size to send pictures and photobucket is laggy to upload 30 at 1 time and automatically downsizes them. 

So what are my options? FTP? If so, what would you guys recommend as far as FTP programs? I'm running Ubuntu Feisty, she's running XP Home. Can I get a free recommendation for each platform? Unless there's a better option than FTP...

---

### Post by SoulinEther on 2007-06-15
Photobucket only downsizes if you don't have it set to the 1 MB limit option, or if your pictures are greater than a meg each, which is likely.

FTP is good, yeah.

---

### Post by Yoooder on 2007-06-15
Setting up an FTP server on one or both machines would probably be the best answer.  Both OS's can run FTP servers fine, and it will really come down to your preference of management.  

Linux has a multitude of good FTP servers, and nearly all will quietly run in the background after being setup, without you having to keep a window open or an item in the task bar.  Windows FTP servers tend to be GUI driven, and some are terrifically easy to setup and use--although they are usually a bit of a pest as they need to be either left running on the desktop (or in the system tray) or started/stopped as needed.
Basically, if 1 of the two of you sets up an FTP server then the other can just login and upload their photos and download the photos already on the server.  Whoever is running the server will have those files stored in whatever folder is shared by the FTP server, and can use the files as normal.

Just do some research, in linux there's ftpd, proftpd, and vsftpd (and about 1000 more), and if you google something like:
> +Windows +Free OR +Freeware +"FTP Server"
it should give you some good results to choose from.

FTP is also an old protocol, and there is mountains of tutorials/docs for it.  So with some googling you should find most answers.

---

### Post by SoulinEther on 2007-06-15
I set up an ftp server on my home server.... vsftpd ran it.

Now i need to figure out how to set up a Linux/Unix/whatever network. :S

Unless you want to buy hosting (which might be a better option if you don't have static ips), set up an FTP server.

---

### Post by morningboat on 2007-06-15
Yes, FTP is a good solution due to its speed and security. The only reason not using it is current solution's complex configuration, but there is an easy solution for FTP now: I'd recommend you use CrossFTP since its simple and easy setup, and it runs on both of your operating systems, since it is cross platform. Here is an [online guide]("http://www.crossftp.com/server_guide.htm") for you to easily setup your server and client. In 5 minutes you should be able to make it.

You can install the server and client just by mouse click (Sun Java required):
CrossFTP Server: [Web Start]("http://www.crossftp.com/crossftpserver.jnlp")
CrossFTP Client: [Web Start]("http://www.crossftp.com/crossftp.jnlp")

Hope this will solve your problem easily. You should have a try.

---

### Post by bobbocanfly on 2007-06-15
For my FTP server i use Proftpd with the Gproftpd GUI control panel.

For a windows FTP server, my friend recommends Filezilla Server but i have never used it, because i never use Windows :D

---

### Post by Roasted on 2007-06-15
> **Yoooder said:**
> Setting up an FTP server on one or both machines would probably be the best answer.  Both OS's can run FTP servers fine, and it will really come down to your preference of management.  

Linux has a multitude of good FTP servers, and nearly all will quietly run in the background after being setup, without you having to keep a window open or an item in the task bar.  Windows FTP servers tend to be GUI driven, and some are terrifically easy to setup and use--although they are usually a bit of a pest as they need to be either left running on the desktop (or in the system tray) or started/stopped as needed.
Basically, if 1 of the two of you sets up an FTP server then the other can just login and upload their photos and download the photos already on the server.  Whoever is running the server will have those files stored in whatever folder is shared by the FTP server, and can use the files as normal.

Just do some research, in linux there's ftpd, proftpd, and vsftpd (and about 1000 more), and if you google something like:

it should give you some good results to choose from.

FTP is also an old protocol, and there is mountains of tutorials/docs for it.  So with some googling you should find most answers.

Wait, not completely sure I understand. Are you saying I can set up FTP on my machine and just have her share out a folder? That way I'd essentially control the uploading/downloading, and all she'd have to do would be to go to her shared folder and see what's there. Right? 

If we could do that, that'd be GREAT. The last thing I want to do is bloat her laptop at all, since it already qwirks out every now and then. I'd like to make it as easy on her end as possible, whereas on my end I'll do whatever I need to to get it running.

---

### Post by Warpnow on 2007-06-16
FTP is waaay to complicated, expensive (kinda), and complex for what you need.

Get a gmail account and use the gdrive application for windows and I forget the name of the linux version. Like 5 gigabytes of space and it shows up as drive G: on your computer.

There is also X drive, not sure if there is a linux version of the app or if it runs in wine, but could be tried. I just use G drive.

All it does it email the file to you. But it keeps you CONSTANTLY connected so you can view your files like its on a HD on your computer.

---

### Post by Yoooder on 2007-06-16
> **Roasted said:**
> Wait, not completely sure I understand. Are you saying I can set up FTP on my machine and just have her share out a folder? That way I'd essentially control the uploading/downloading, and all she'd have to do would be to go to her shared folder and see what's there. Right? 

If we could do that, that'd be GREAT. The last thing I want to do is bloat her laptop at all, since it already qwirks out every now and then. I'd like to make it as easy on her end as possible, whereas on my end I'll do whatever I need to to get it running.

Yeah, if she sets up an FTP server on her machine, and creates a login for you that points to the folder she would like to share then you can login to that folder and upload/download from it at your will.  She could negate having to use an FTP client and just keep using the folder as normal.  So yes, basically you would be in charge of what you place into that shared folder on her machine as well as what you take from that shared folder.

In regards to the static-ip comments.  Just go to dyndns.org and setup an account.  You download a small utility that will keep a domain pointed to the server-ip regardless of whether that IP stays the same or changes (so instead of 141.243.10.32 you can just use the easier address of "yoooderFTP.dyndns.org" or whatever you choose).

---

### Post by Warpnow on 2007-06-18
Like I said, too complicated for 2 people wanting to share files...a waste of effort.

---

### Post by crimesaucer on 2007-06-18
> **bobbocanfly said:**
> For my FTP server i use Proftpd with the Gproftpd GUI control panel.

For a windows FTP server, my friend recommends Filezilla Server but i have never used it, because i never use Windows :D

I liked Filezilla on my Windows when I was teaching myself xhtml/css web design, it always worked well with my web hosting and my ISP web space.

I stopped making my practice xhtml/css web pages so I barely use FTP on xubuntu. Since I only use FTP here and there, I didn't feel the need to install FileZilla in Wine, so I use FireFTP and it works good....not as good as FileZilla but good enough.

---

### Post by dmizer on 2007-06-18
the absolute easiest i can think of for your girlfriend's point of view anyway ... would be to set up a lamp server, and host gallary: [http://gallery.menalto.com/](http://gallery.menalto.com/)

to get it set up, it would be some work on your end.  but for her ... all she would have to do is log in, and upload pictures.

---

### Post by Warpnow on 2007-06-18
Yeah, from his gfs pov it'd be easy, but from his its hours of server configuration, constantly keepiing that server running, and the necessary maintenancy that comes with it...

If you did go with ftp, it'd be worth your time to get some hosting to not run the server. bluehost.com offers 300gigs for 6.95 a month, hostmonster the same for 5.95.

But its really unnecessary. Get G drive or X drive and you've got around 5 gigs in both for free.

Also check out: [http://www.streamload.com/](http://www.streamload.com/)  25 gigs of free online storage.

An FTP server  is not the way to go for such an easy to accomplish task....

---

### Post by chio on 2007-06-18
Why not just use Flickr? It doesn't downsize the images unless you ask it to and you can upload as many as you want at once...

---

### Post by frodon on 2007-06-18
> **Warpnow said:**
> FTP is waaay to complicated, expensive (kinda), and complex for what you need.Any argument maybe to justify this ?, not that i don't agree with this but without any argumentation this kind of comment has really no value.

> **Warpnow said:**
> Get a gmail account and use the gdrive application for windows and I forget the name of the linux version. Like 5 gigabytes of space and it shows up as drive G: on your computer.

There is also X drive, not sure if there is a linux version of the app or if it runs in wine, but could be tried. I just use G drive.

All it does it email the file to you. But it keeps you CONSTANTLY connected so you can view your files like its on a HD on your computer.

Gmail is good except on the level of privacy, don't expect any kind of privacy using gmail services, every single mail you send or service you use through gmail is processed so your privacy level is near of 0 but like i said except this "little" drawback gmail services are just damn good.

---

### Post by dmizer on 2007-06-19
> **Warpnow said:**
> Yeah, from his gfs pov it'd be easy, but from his its hours of server configuration, constantly keepiing that server running, and the necessary maintenancy that comes with it...
i gave the suggestion based on this comment:
> **Roasted said:**
> I'd like to make it as easy on her end as possible, whereas on my end I'll do whatever I need to to get it running.
gallery is not that difficult to set up and maintain, and i think it's extremely easy to use.

i do agree that ftp is overly complex for this though, particularly from the girlfriend's point of view.

---

### Post by scxtt on 2007-06-19
why not use ssh (sftp) and have her use some client (like filezilla) that can connect via sftp/ssh2? ... all you'd have to do is install ssh-server (easy, no config necessary) and create an account for her (like /home/<your GFs name>) and make a p/w for it ... then just put pics there and she can get them when she wants and put new ones there ...

---

### Post by Warpnow on 2007-06-25
Gmail's privacy issues are unimportant to me because I don't intend to put an illegal file in an email, and that's the only way I'd be concerned. Their software searching my text to build their ad engine is, really, not a concern for me. So some computer knows what kind of porn I like? Big deal ^_~

---

### Post by frodon on 2007-06-25
> **Warpnow said:**
> Gmail's privacy issues are unimportant to me because I don't intend to put an illegal file in an email, and that's the only way I'd be concerned. Their software searching my text to build their ad engine is, really, not a concern for me. So some computer knows what kind of porn I like? Big deal ^_~Fortunately not everyone think in a personal way otherwise our whole privacy on internet wouldn't even exist.
I use gmail as well for mailing lists and BTW keeping your privacy is not about hiding you and what you do but it's another completely different  discussion for sure.

---

### Post by Warpnow on 2007-06-25
I don't disagree with a right to privacy, but I don't think gmail violates that right. And, if they do, you can realize the benefits of their service with certain applications while leaving it for others.

---

### Post by H.E. Pennypacker on 2007-06-25
FTP is good in concept, but it wouldn't work well, in my opinion.  I've used a bunch of FTP clients on both Windows and Ubuntu, and I have never really been comfortable with anyone of them.  They are all pretty much the same, and I find them all unnecessarily slow.  My website has CPANEL, and I like to use its file manager for uploading files.  It's much easier, and faster.

For you, I'd suggest using direct connect with an instant messenger.  I know you said you have Pidgin, and she has something else, but try another IM application then.  Regardless of which IM application you use, direct connect is the easiest and most practical way of transfering files between the two of you.  If your girlfriend is not into computers, she really won't have to worry, and things will be easier for you as well.  Try Kopete or other KDE instant messengers.  I don't know what Kopete is like.  I am just throwing you a name.

---

### Post by samschoice on 2007-06-25
Hey PennyPacker,
Have you tried using FileZilla?  You can find it in your synaptic package manager. I can't imagine running a site off of cpanels file upload functions.

---

### Post by H.E. Pennypacker on 2007-06-25
> **samschoice said:**
> Hey PennyPacker,
Have you tried using FileZilla?  You can find it in your synaptic package manager. I can't imagine running a site off of cpanels file upload functions.

The file manager is great...I can't imagine why I would want an application to handle uploads.  It makes no sense to me at all.  FTP clients require you to log in, and do things that are unnecessary.  The file manager makes it a breeze, and much faster.

---

