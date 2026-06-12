---
title: "Looking for Home Server Advice"
date: 2010-07-05
forum: The Cafe
---

### Post by chessnerd on 2010-07-05
I am going to be setting up my first home server system later this month. It will be used for file storage and to share files between members of my family. However, I have never managed a server before. I was hoping that some of you guys who have would be able to share with me some of your wisdom.

The server itself will be an old Dell Optiplex with these specs: 1.8 GHz Pentium 4, 512 MB RAM, and 120 GB HDD split between a 40 GB drive and 80 GB drive. I'm currently considering Ubuntu 10.04 or Debian Lenny as the distro. 

General advice about managing a Linux home server would be great, as I have almost no idea what I am doing. Also, links to some good how-tos and informational websites would be nice. Suggestions for books would be welcome, too.


Also, there are some things specific to my set up. If there is any way you could help me with them, I'd be grateful...
1. I will not be living at home while at college. This means that it could run for a week or two without any maintenance. Thoughts?
2. My family doesn't really know much about servers, Linux, or computers in general. However, I want them to be able to use this without too much hassle. What are some ways that I could make using this server easier for them? They will be accessing it from Windows machines.
3. It may be headless, so it would be nice if I could manage it via SSH (or something similar) from local machines. How would I set that up?
4. I would like each of the family members to feel safe about storing and backing up information on the server. Is there a way I could set up folders with passwords or something similar? It would need to be easy to use (no command-line stuff) and it would be done through Windows machines.

---

### Post by undecim on 2010-07-05
You will need to set it up with SSH and Samba at the very least.

Forward your SSH port. If you have a router that will let you forward an external port to a different internal port, you won't have to change any SSH settings, just choose a port > 10,000 or so and forward it to your server port 22. That way, you can SSH into the server while at college. If you can't forward ports with different numbers like that, then you will need to change the port on your server in /etc/ssh/sshd_config.

You will want a dynamic DNS service if youd don't have a static IP address (home internet services usually don't). I use freedns.afraid.org for mine. You will want to set your server up to update once per day. Freedns has a wget script that is written for Windows, but the wget line from the script will work in a Linux script, so add that to a cron job to run at night.

That should make it so you can connect to it from outside your network. Now, as for sharing files, you will want to use Samba. You also need to add an account for every person who will be storing files in a private directory.

This will let your family go to "\\SERVERHOSTNAME\username" in a windows file browser to get to the files in their home directory with a username/password.

Also, look at setting up RAID 1 and getting an off-site backup if you want permanent storage.

---

### Post by NCLI on 2010-07-05
Setting up a fileserver and letting it run on its own for weeks is easy, the only hard part is setting up SAMBA. It's a bitch, I still haven't managed to get it to work.

While at college, you can access your server using SSH.

---

### Post by CharlesA on 2010-07-05
I used Webmin to set up Samba, since the configure is a pain in the butt if you do it via editing conf files.

SSH works for config.

```
sudo apt-get install samba ssh
```

Just be sure to secure SSH using iptables and use a strong password or keys.

---

### Post by drdos2006 on 2010-07-05
Check this out, I found it very useful.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by Warpnow on 2010-07-05
Webmin is pretty easy to use.

---

### Post by chessnerd on 2010-07-05
Thanks guys. 

I've had plenty of problems with doing the Samba in the past, not to mention the issues I've had setting up networking with Windows machines. ;) So I'll definitely take a look at Webmin.

@drdos2006 - That how-to looks perfect for what I am planning on setting up. Bookmarked!

@undecim - If you had posted that a few months ago, I wouldn't have understood a word of that. :) I still don't know how to do most of it, but I'm sure Google will give me the answers.

That free DNS service looks useful. As you have correctly guessed, I do not have a static IP (I have Comcast). Again, I'll need Google to figure it out, but I had no idea where to start in the first place, so you've moved me several steps in the right direction. Thank you.

---

### Post by Yarui on 2010-07-05
If you are looking to learn more about servers in general, I have found this guide to be extremely informative in the past.

[http://www.aboutdebian.com/](http://www.aboutdebian.com/)

It recommends using Debian, but even if you don't end up using Debian the information is still relevant.  The guide is extremely detailed so if you are the type to read something from beginning to end without skipping around it could take you quite some time to read, but it's seperated into sections and subsections pretty well so it shouldn't be difficult to skip to the information you need.

---

### Post by blueturtl on 2010-07-06
You may want to look in to NFS as an alternative to Samba. It is so much less complicated to set up. Only downside is that Windows clients won't have native support for it. Still, if there is an installable add-on for the Win clients it might be easier to use than trying to get Samba to work properly.

I went the Samba route, it is a pain in the rear. I have no idea why Microsoft had to make things so complicated over what seems so simple in principle.

edit: Check this out for instance: [http://ubuntuforums.org/showthread.php?t=310168](http://ubuntuforums.org/showthread.php?t=310168)

---

### Post by 3rdalbum on 2010-07-06
I don't get why people say Samba is hard to set up. It's only hard to set up if you try to do it using configuration files.

Ubuntu ships with a GUI called "shares-admin" that helps you to set up Samba shares. For the slightly more advanced, the repositories contain "system-config-samba" which I personally use. For anything more advanced... well, you're probably running an enterprise server anyway which would be headless.

---

### Post by blueturtl on 2010-07-06
> I don't get why people say Samba is hard to set up. It's only hard to set up if you try to do it using configuration files.

It's not the actual set up bit, even with config files. It's the fact there's no guarantee things will work even after everything has been properly set up. One day everything will appear to work fine, next day none of the computers can see each other.

Instead of the horror that is "master browser wars" I prefer the simplicity of of /etc/shares and /etc/fstab. Everything is hooked up via IP addresses. No fuss, no muss.

---

### Post by CharlesA on 2010-07-06
You had problems with name resolution then?

I ended up having to run a dns server on my network (on my router and let it keep the database updated) and now it works fine for me.

---

