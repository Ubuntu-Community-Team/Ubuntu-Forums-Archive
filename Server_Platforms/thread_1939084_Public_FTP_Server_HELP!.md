---
title: "Public FTP Server HELP!"
date: 2012-03-10
forum: Server Platforms
---

### Post by Hank_The_Dog on 2012-03-10
So I have this lovely samba share I use around the house. The only thing is I am being sent out of town for work on Monday. I need a way to access my local server from a remote connection. I have no experience with SSH, so FTP seems like my best option.

Basically I have the directory "/server/share/" that is used for my samba share, on a local dedicated computer.

It would be great if I could just 'ftp://my.ip.add.ress' to get files.

I already forwarded port 21 on my router to go straight to my server.

Stumped. Whats next?

Any help would be great.

---

### Post by papibe on 2012-03-10
Setting up sftp is that simple, and it would be far much safer.

You install openssh-server, forward de port 22. and that's it. You will not only have access to your files, but the possibility of having shell access via ssh.

I would recommend giving it a try.

Just some thoughts.
Regards.

---

### Post by Hank_The_Dog on 2012-03-10
Thanks for the quick response,

So what you are saying is install  openssh-server. And forward port 22 on my router to my server?

Seems easy enough

Questions:

Where/how would I specify what folder(s) are shared? And how would I access it remotely?

---

### Post by papibe on 2012-03-11
It basically will give you access to your home directory, and everything that your local user has access to it.

Regards.

---

### Post by lykwydchykyn on 2012-03-11
If you're accessing it from a Linux machine, most file managers (nautilus, pcmanfm, thunar) will take a url like this:

ssh://ip.of.my.machine/some/path/on/remote/system


In KDE, dolphin will do something similar, but the protocol is fish:// for some reason.

From a console, you can use a number of tools, like ssh (for shell access), scp or rsync (for copying to/from the machine), or sftp (for ftp-like access).

From Windows, you need something like WinSCP installed, which will give you an (graphical) ftp-client like access to your entire system.

From a Mac, I have no idea, but surely they've something on there since it's unix.

---

### Post by bubylou on 2012-03-11
Also to install openssh you can use either tasksel or use apt-get install openssh-server. You might also want to increase openssh security if your going to open it to the world. Such as key authentication since guessing a simple password isn't much.

---

### Post by Jonathan L on 2012-03-11
> I have no experience with SSH

Hi Hank

However, I really truly echo the comments of the others above: use ssh instead.  It's actually a bit easier to do than FTP, in general, and in my experience works in more hotels and public wifi places than FTP (which sometimes is blocked or needs passive mode).  The average hotel or conference network is horribly open too, and the ease of seeing your FTP password should make your toes curl.

I've used FTP for very many years and still see quite a few benefits to it; nonetheless I'd recommend you don't use it for what you're doing.

Make the jump, you'll not regret it.

Hope that's helpful..

Kind regards,
Jonathan

PS.  And if you find yourself thinking you really just want something quick and nasty and simple (and open) for the occasional file, I'd recommend HTTP (with apache) and simple htpasswd functions.

---

### Post by Hank_The_Dog on 2012-03-11
Thanks all! Great help.

I tried tinkering with it last night, but I believe I am going to make the switch to SSH, and finish the project today.

I am going to start googling SSH tutorials now. Any good ones you know off the top of your head that would be helpful?

Thanks again.

---

### Post by papibe on 2012-03-11
I thinks this is is a good one: [Beginning SSH on Ubuntu]("http://principialabs.com/beginning-ssh-on-ubuntu/").

As mentioned before, the basic steps to get it working are not as much as discussed already, so there's no need to strictly follow the directions on the tutorial.

However as bubylou recommended it, as I do too, take a look at the section "Public-Key Authentication".

Hope it helps, and tell us how it goes.
Regards.

---

### Post by Hank_The_Dog on 2012-03-11
Wow, that was easy. :)

So I now have root access to the my server from a remote connection.

Next question(s) for you wizards.

How would I go about copying files from my server to my local hard drive?

Also random question kind of off-topic,
My server has a dynamic IP address. How can I set up a static IP? Every-time I try to change it graphically, my Internet connection gets screwed. 

I am just tired of changing my port forwarding every time we lose power.

Thanks!!
:D:D:D

---

### Post by Hank_The_Dog on 2012-03-11
> **lykwydchykyn said:**
> If you're accessing it from a Linux machine, most file managers (nautilus, pcmanfm, thunar) will take a url like this:

ssh://ip.of.my.machine/some/path/on/remote/system



Woah, my question was already answered.

This has been a lifesaver guys.

---

### Post by kevdog on 2012-03-12
sftp is what you want to use to transfer files.  This can be done over the command line if you want -- it works similar to ftp (get,put, etc). 

If you need to transfer a lot of files I usually just use rsync -- that utilizes ssh on the backend.

For your IP problem, register with a dynamic IP address utility such as noip.com -- there are other as well.  That way you can connect by name rather than ip number.

Lastly -- now that you are running a server (good job), you might want to discover ways to harden the server to outside penetration.  With ssh, this can be done with the use of keys, restricting access to named users or groups (within the sshd_config file) or globally on the computer by altering firewalls.  Usually its best to implement many of these strategies simaltaneously.  I'm just mentioning this -- although its not mission critical -- its just something you might want to start looking into.

---

### Post by Hank_The_Dog on 2012-03-12
Kevdog,

Thanks for the kudos. And I am researching security techniques now.

I think my IP question needs to be re-worded. (But noip.com looks like a great resource, thanks for the tip.)

Basically I would like to change my local IP address on my server from 192.168.1.X to 192.168.1.198

I just am not sure how to do that.

Thanks again guys... openssh is slowly changing my life already!!

---

### Post by lykwydchykyn on 2012-03-12
Is this desktop Ubuntu or Ubuntu server edition, or some other Linux?

---

### Post by Hank_The_Dog on 2012-03-12
Ubuntu maverick...

---

### Post by bubylou on 2012-03-12
Bookmark [this page]("https://help.ubuntu.com/11.10/serverguide/C/index.html"). Go to networking for your static ip needs.

---

### Post by Hank_The_Dog on 2012-03-15
Thanks all! It was a terrific week out of town, and my server worked exactly as I needed!

Thanks again.

---

