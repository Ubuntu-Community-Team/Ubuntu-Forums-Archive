---
title: "Some questions regarding hosting website on a local computer and attaching files."
date: 2012-11-26
forum: Server Platforms
---

### Post by rhexis07 on 2012-11-26
Hello.
 
I am not sure if I'm in the correct forum, or if my the title of my thread is clear enough. But I do hope I can get some help from you kind gurus.
 
I have been asked to come up with a solution to solve an issue in the company. Right now, staffs are all using e-mails to attach their files, and cc-ing them to all relavent parties. The key person who will read the e-mail will read, make some changes, and inform the person who has sent it to them through e-mail that the things required have been done. 
 
As our Lotus Notes e-mail is really slow at times, it some times take up to 3-5 minutes to open a file of 5MB size. It slows the network a lot as well with all the e-mail sending here and there.
 
I have proposed using an intranet where user logs in and attach their files, and the admin will be able to log in and retrieve these files and do the necessary stuffs. I do have some knowledge on this, but I am really new to the hosting side.
 
I have read some topics on hosting the website on a computer locally, and I believe that may not be such a big problem.
 
What I do wish to know is, how should I get the user to attach their files?
 
 
 
Since I wish to host the file locally on my computer (Company policies might restrict me hosting it on the server), how should a user attach a file and allow the admin to download it?
 
Basically, what I want is to eliminate the use of e-mail in this case, and have everything done by attaching and downloading. Something like Dropbox. I do apologize if you do not understand my question, and if there's any confusion please let me know and I'll do my best to repharse everything.

---

### Post by sandyd on 2012-11-27
I have the perfect solutions: OwnCloud.

Works very well, and is built by the KDE Team.

---

### Post by thnewguy on 2012-11-27
I second that. A small server with ownCloud installed would probably be any easy way to go. You can upload all your files there and collaberate. Just send users a notice saying the file has been shared with their account.

---

### Post by SlugSlug on 2012-11-27
I third that :) owncloud is pretty cool

---

### Post by rhexis07 on 2012-11-27
Hello Gurus,

thank you for your prompt reply and suggestion. I have taken a look at owncloud and am downloading it to try. 

However, my company has some strict policies about downloading and installing 3rd party software. But I will discuss this with my supervisor to see if there can be an exception made.

May I ask though, what are the stuffs I need prior to setting up this owncloud? I'm actually more of a Java and SQL programmer, and this is actually the first time I'm venturing into the web server. I'm keen in learning this, and will be talking to my supervisor to give me a computer to try to set this thing up. (Currently an Industrial Attachment student is reading up on HTML and SQL and all the stuffs needed to build a website for this feature).

It is mentioned on OwnCloud download that I need a webserver. I suppose this would be the Apache that I've read along the way somewhere am I right? 

I don't wish to use a dedicated machine, meaning that I hope I'll be able to use a working PC to act as a webserver. Is that possible?

I'm sorry for the amount of question asked, but I'm really keen in this and would love to get a good kick start from you Gurus.

---

### Post by JKyleOKC on 2012-11-28
> **rhexis07 said:**
> However, my company has some strict policies about downloading and installing 3rd party software. But I will discuss this with my supervisor to see if there can be an exception made.Remember that to serve up web pages via HTML, you must install something like Apache -- and that, in itself, is 3rd party software. An exception will be necessary to do anything of this sort!

---

### Post by rhexis07 on 2012-11-28
Hello Kyle,

Thanks for your reply. I understand. I will discuss with my supervisor regarding this matter. I will propose using a complete stand alone PC to do everything first before joining it to the network.

I've read on ownCloud that to run it, I will need some Apache stuffs. I suppose this means that even before installing ownCloud, I would need something like Apache to kick start?

Once again thank you for your time and replies. It's helping me to understand the entire web server structure better.

---

### Post by SeijiSensei on 2012-11-28
Are you a Microsoft shop?  Have you looked into Sharepoint?

The other obvious and simple solution is just to set up a file share on a server or even a Windows desktop machine with sufficient available storage.  Create permissions that allow ordinary users to write files there but not read them then grant the admin full privileges.

Rather than trying to install something no one in your organization has any experience with (Linux, Samba, Apache, etc.), and which your organization's policies might prohibit, why not just use what you already have?

Despite my long-standing commitment to Linux, it's not the right solution for everyone.

---

### Post by rhexis07 on 2012-11-30
Hello Sensei, good teacher, lol.
 
Anyway, I don't understand your term by Microsoft Shop, but if you mean my company uses Microsoft primarily, then yes, we are.
 
I have not looked at Sharepoint, but I will definitely give it a look together with ownCloud.
 
I did propose setting up a file share on the server, but there is a concern raised from the admin as he does not want to go through every folder checking which file came first and which file came second. He wants to log in to something, and all the files just appear at the page immediately, sorted by the earliest submitted to the latest submitted.
 
As there is a possiblity that many folders appear in the Main folder, such as Classified, Unclassified, Project A, B, C, D...001, 002, etc, he doesn't want to go through the hassle of checking every folder to see which has been uploaded first.
 
I will be starting this project hopefully next week, just a trial though. I requested to install software and have been approved.
 
However, I will greatly appreciate if someone could direct me to a proper tutorial on how to upload a file to a server through an intranet. The server, in my case, would be a local computer. I want the users to connect straight to the computer and not into the server.
 
I hope I'll be able to get a reply regarding this matter, because I'm actually starting to feel a little excited as I haven't done a project in a long time.
 
Thank you all gurus again for your help and patience. If there are parts that you do not understand, do let me know and I'll try my best to rephrase my problem better.
 
EDIT:
 
I just googled some more and found out that you need PHP to upload stuffs. I've played around and am however stuck at this.
 
When I click on upload on a HTML source, it asks me to download the php file that I created, instead of uploading it to my computer. (Just doing a quick test as of now.) I am still troubleshooting, but if anyone can guide me through this I would greatly appreciate it. I've never touched PHP before. :(
 
DOUBLE EDIT:
 
Just realised to run a PHP file I have to have the Apache installed, which I have not. So I guess until I have my dedicated PC, I will not be able to do some proper testing. If I am wrong please let me know. :) Thanks again!

---

### Post by pkadeel on 2012-11-30
> **rhexis07 said:**
> 
As there is a possiblity that many folders appear in the Main folder, such as Classified, Unclassified, Project A, B, C, D...001, 002, etc, he doesn't want to go through the hassle of checking every folder to see which has been uploaded first.
I have no experience with owncloud but that was suggested by some experienced members here so that will be a good solution. What basically you need here is

[LIST=1]
[*]A web server
[*]A web page accepting file uploads
[*]A web page presenting uploaded files in a chronological order
[*]A back-end script which can handle file check in and check out.
[/LIST]
Don't get confused with the terms web server and web page because as far as a web server and a web page is concerned, internet and intranet are same. The only difference is that an intranet only web server is not visible to outside world whereas an internet webserver is visible on web.

  > **rhexis07 said:**
> 
The server, in my case, would be a local computer. I want the users to connect straight to the computer and not into the server.
 
You mean your local computer which is connected to an intranet will act as a server? What do you mean by saying "Connect straight to the computer and not into the server." because both are actually same.

---

### Post by pkadeel on 2012-11-30
> **rhexis07 said:**
> 
DOUBLE EDIT:
 
Just realised to run a PHP file I have to have the Apache installed, which I have not. So I guess until I have my dedicated PC, I will not be able to do some proper testing. If I am wrong please let me know. :) Thanks again!
My suggestion is to keeps things as simple as possible. First define what you already have

[LIST=1]
[*]A computer with an OS (that is for sure you have)
[*]Depending on the OS you have option which web server to prefer.
[*]Depending on OS and your experience with web scripting which language to prefer i.e. PHP or ASP
[/LIST]

---

### Post by SeijiSensei on 2012-11-30
> **rhexis07 said:**
> I did propose setting up a file share on the server, but there is a concern raised from the admin as he does not want to go through every folder checking which file came first and which file came second. He wants to log in to something, and all the files just appear at the page immediately, sorted by the earliest submitted to the latest submitted.

If everyone shares a single directory, there is only one folder to review.  Sorting the files by date is as simple as opening the folder in Windows with a detailed listing and clicking on the date column.

In Samba, I would create a share that is owned by the admin but to which everyone has write privileges but not read privileges.  The admin would have full privileges, of course.

How you manage users and groups depends on the infrastructure of your network.  If you have a Windows domain controller or use Active Directory, Samba can use these to authenticate users and grant privileges accordingly.

However if everything happens through Notes, you might have bigger issues.  When you start up a Windows workstation and log in, how is the user authenticated?

Also rather than reinventing the wheel, you could install one of the various PHP-based file managers.  Here's a [list of options]("http://kdelchev.com/2012/01/php-file-managers-projects/").

---

