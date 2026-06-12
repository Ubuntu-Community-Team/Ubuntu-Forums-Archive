---
title: "How to add a user that can only upload and download files from my webserver?"
date: 2009-01-19
forum: Server Platforms
---

### Post by Master_God on 2009-01-19
Hi,
I want to set my friend a user so he can use my server to host his website.

How can I accomplish that? Thanks.

---

### Post by Thirtysixway on 2009-01-19
You can setup something like mod_dir if you're using apache and give him ftp access.  Just configure ftp to lock users to their home directory, and give him a public_html folder to put his stuff in.

Since he's your friend I wouldn't worry too much about securing the system completely, just make sure he's not uploading anything that's potentially exploitable and fatal to the system.

---

### Post by Master_God on 2009-01-20
You make it sound so easy but I have no idea how to do such stuff..;)

---

### Post by hyper_ch on 2009-01-20
host his website or does he just need storage space?

---

### Post by Master_God on 2009-01-21
> **hyper_ch said:**
> host his website or does he just need storage space?

What's the difference?
Hosting his site means his files would sit on my server and "storage space" means his files would sit on my server..

---

### Post by hyper_ch on 2009-01-21
hosting means having his files on your server and make them publicly availble...

---

### Post by aaron.d on 2009-01-21
It is clear that 'hyper_ch' did not take the time to read your post, as the dialogue sans extraneous info goes like so:

**Master_God**
>  I want to set my friend a user so he can use my server to **host his website**.

**hyper_ch**
>  **host his website** or does he just need storage space?

which comes off a tad insulting. However, a web server and a file server are not *necessarily* the same thing. 

All web servers(speaking in generalities) are file servers, but not all file servers are web servers. 

Say you friend wanted a place to store all his pictures of pretty people and his "art films" - because he uses his moms computer at home and she just doesn't appreciate the fine arts. 
Well, he could stash that **** at your place, and you could set up a file server that can be accessed to store and retrieve data. there are tonnes of ways to do that:

smb(samba),ftp,scp/sftp,nfs...

But in this case, you are serving files, not hosting a website.

Now, if you really wanted to do a public service, you WOULD build a website, because "art" that great would surely command the widest audience possible. That would be a web server AND file server.

Hopefully you get the point, and if it's something you already knew, then I trust you will enjoy the hypothetical anecdote.

p.s.

I have zero apache skills, aside from straight up single domain/single site, so I don't know the answer to your original question.

p.p.s

It is early here, sorry for hijacking you thread with my ramblings.

p.p.p.s

you started it.

p.p.p.p.s

or maybe the other guy started it, but you kept it going.


...

---

### Post by hyper_ch on 2009-01-21
> **aaron.d said:**
> It is clear that 'hyper_ch' did not take the time to read your post
That's an assumption on your side ;) I did and it's not clear what the TO actually wants ;)

---

### Post by Master_God on 2009-01-21
Hehe, thanks but I'm not offended in any way.

So, after understanding what I wish to do, how can I accomplish that?

P.S
I case someone still don't understand I wish to let my friend host his site on my web server (using Apache2) and upload & download files (like the site's HTML files or anything he needs for the site).

Little brief:
Vanilla Ubuntu Server v8.10 Installation under VMware having Windows XP as the host OS.
I have Webmin installed.
"It works" is available from the net.
I have no clue what so ever in such business so please be gentle ;)

---

### Post by RonWill on 2009-01-25
I have the same question, sort of. I'm a noob and have installed 8.04 LAMP on an old intel 810 machine. Runs great. I have a home network behind a Linksys WRT54GL router with earthlink as ISP. Set a fixed IP address for the ubuntu box and have installed Samba. I can see my other Windoz machines and shared directories on them. Have created a Public directory under my /ron/ directory and successfully shared that to my Windoz workgroup. I have managed to edit the index.html file in /var/www/ and can see that when I use the fixed IP in Firefox. The server is only a test platform on my home network so I can practice some code that will eventually be used on an actual server hosted on the web. My present workaround is to load files to the public directory and then sudo cp them from that into www. That works but is ugly. I tried sharing the /var/www/ directory and got the "not owner" message. I'd like to be able to set up FireFTP (already use that to upload to the outside server) to upload to my local /var/www/ directory so I can easily transfer files. I installed ssh but don't know how to set up a user account to ftp into. Any help will be greatly appreciated.

---

