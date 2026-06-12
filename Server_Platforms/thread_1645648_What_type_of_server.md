---
title: "What type of server?"
date: 2010-12-14
forum: Server Platforms
---

### Post by CadmiuM1337 on 2010-12-14
Hi Guys,

Firstly, Thank you very much for reading this post and possibly answering my question. I've asked everywhere and have yet to obtain a decent answer.

So my girlfriends father gave me and old pc. It's got ~1gb of RAM and around 35gb of hard drive space on it. 

The question I'm asking is if it was possible to somehow turn this computer into a server of sorts for storage that I can access from my other computers in my house as well as other places. Possibly tell my friends to connect to it from their computers to download a file, etc (With a password, ofcourse)

I realize this is a Ubuntu forum, but i'm sure this forum is very knowledgeable in other fields, such as a suggestion to what works the best for my situation.

Obviously, I plan expanding the hard drive space. So hard drive space is not an issue.

Thank you again,

Lance

---

### Post by CharlesA on 2010-12-14
Yes. Ubuntu will run fairly well on a machine with those specs.

Did you just want it as a media server, or file server?

---

### Post by CadmiuM1337 on 2010-12-14
Ahem, I'm embarrassed to ask, but what's the difference?

I would assume a file server, I will be storing media files such as much and videos, as well as documents too.

Thank you very much for your extremely quick response.

Lance

---

### Post by CharlesA on 2010-12-14
Same thing, pretty much.

Are you going to be serving Windows machines, or other Ubuntu boxes?

---

### Post by CadmiuM1337 on 2010-12-14
I would be serving other Windows machines. I heard something about setting up an FTP server, but I wanted to get advice first.

If there is an easier process or a more efficient way of doing this on something other than Linux? (Doubtful, but worth the question all the same)

Thank you.

Lance

---

### Post by CharlesA on 2010-12-14
I know you can run something like Windows Home Server, but you'd have to pay for it and it can do pretty much the same things you can do with Linux (with a little bit of reading).

Depending on what version of Windows your clients are running, you can look into Samba (all versions) or NFS (Win7).

As for sharing with other people, I'd suggest not using a pure FTP server, as the transfer is not encrypted and passwords are sent in cleartext.

When you say that you want yer friends to be able to access yer server, what do you mean?

---

### Post by CadmiuM1337 on 2010-12-14
Linux seems a lot more lightweight, and I don't mind reading up on how to operate it either. This is actually an interesting project i've been wanting to do for quite some time.

By letting my friends connect to it, I meant if there is a way that my friends can somehow access it from their computers (or anyone really, maybe connecting to some sort of ip and typing in a password)

Would you suggest me to use SAMBA or something that Linux can supply me with?

And PAY for a program to host my server on? Yeah, right!

---

### Post by CharlesA on 2010-12-14
If you want a graphical type thing, there is always this: [http://sourceforge.net/projects/ajax-explorer/](http://sourceforge.net/projects/ajax-explorer/)

Haven't used it myself, but I've heard it's really nice.

Samba would probably work for you if you are running Windows machines other then Win7. Win7 can access NFS after installing something from Microsoft, which is handy.

---

### Post by CadmiuM1337 on 2010-12-14
Awesome! Whenever I setup the old computer I'll let you know how it goes.
Again, Thank you very much for your help.

Lance

---

### Post by CharlesA on 2010-12-14
No problem.

There are a ton of knowledgeable people here, so if you have any questions, or run into problems, make a thread. :)

---

### Post by drdos2006 on 2010-12-15
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

