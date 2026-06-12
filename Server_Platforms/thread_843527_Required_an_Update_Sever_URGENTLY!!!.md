---
title: "Required an Update Sever URGENTLY!!!"
date: 2008-06-28
forum: Server Platforms
---

### Post by rahmath on 2008-06-28
Dear All,

Even though i do have experience in Linux, Ubuntu is a really a new environment for me. I heard about the growing popularity and simplicity about Ubuntu, thats why i didn't say NO to my Manager while he opted to implement Ubuntu in our network.

Now i am really in to trouble. Here we do have few Linux clients running with Ubuntu 8.04. Now i have to configure a centralized update server which will download all updated packages from the internet and store's it in its own hard disk. Then later this packages should be available by push or pull mechanisms to install the update to all the clients.

Our Update server should update itself also. 

When i roamed around in the internet i found two links ([https://wiki.ubuntu.com/NetworkWideUpdates](https://wiki.ubuntu.com/NetworkWideUpdates), [https://wiki.ubuntu.com/UpdateServer](https://wiki.ubuntu.com/UpdateServer)) which shares almost the same idea, but dosent discuss about how to achieve this goal.

So, really requesting someone to help me to get out of this issue. 

Thanks in Advance...

---

### Post by koenn on 2008-06-28
It should be sufficient to edit the /etc/apt/sources.list on your clients so that they point to your update server, which is supposed to be a http or ftp server. 


it's a basically a pull mechanism, but ubuntu can be configured to download and install updates/patches automatically, iirc.

I don't know if an ubuntu server does auto-updates, but you can probably do that with cron. you need to execute apt-get update && apt-get upgrade

---

### Post by slakkie on 2008-06-28
> **koenn said:**
> 
I don't know if an ubuntu server does auto-updates, but you can probably do that with cron. you need to execute apt-get update && apt-get upgrade


On a server you NEVER want to do this with cron. When you update your server via a script in cron you could potentially break a server, cause downtime on applications or worse your complete server. Since downgrading is not an option.. 

Updates should be done manually.

Running apt-get update automaticly (via cron) is a valid option. You are not installing/upgrading packages.

---

### Post by koenn on 2008-06-28
> **slakkie said:**
> On a server you NEVER want to do this with cron. 
Updates should be done manually.

I agree. I'd never auto-update (upgrade) a server.
But one of the requirements in the OP is
> Our Update server should update itself also. 
So I indicated a way in which this **can** be done ...

---

### Post by cariboo on 2008-06-28
Have you considered apt-cache it will cache the updates in a way that your linux computers can access them with the update manager.

Jim

---

### Post by koenn on 2008-06-28
Oops, missed the part where you said  "**have to** configure ... " ; I thought you already had set up some sort of local repository. 

The fastest/easiest is indeed something like apt-cacher or apt-proxy. 
The problem there (at least with apt-proxy) is that it's just a cache of what gets downloaded by any client, you can't hold/approve/release the packages at will

If you run a web server, it can serve as a local repository for packages, and it will only serve the packages you make available. 
Here's a similar question :
[http://test.ubuntuforums.org/showthread.php?p=5221817](http://test.ubuntuforums.org/showthread.php?p=5221817)


And this from an ather thread : 
> **HalPomeranz said:**
> You could use a command like fanout, sshmux, or cluster SSH to run the same apt-get commands simultaneously on all of the machines.

---

### Post by slakkie on 2008-06-28
> **koenn said:**
> I agree. I'd never auto-update (upgrade) a server.
But one of the requirements in the OP is
 
So I indicated a way in which this **can** be done ...

I'm sorry, you are right. 

Although I still would not do this in a production enviroment.

---

### Post by rahmath on 2008-06-29
Thx for all of your nice suggestions,

I agree i can setup a local repository and server and from clients i can point to this local repository server. But frankly i don't know how to exactly download the packages to my local repo server and how to serve them (means is there any special hierarchical way in handling those files).

Once its been clear, i guess by configuring my local repo server as a web server and pointing from my clients to this local repo WEB server will do the task for me.

Also i don't understand about the issues which might cause during an automatic update. 

Thx in advance...

---

### Post by rahmath on 2008-06-29
One more thing to add...,

Up to this time i was sticking on to a technical term "Update Sever" and was flowing around the internet with this keyword. Thats why i was not able to get in to the correct idea.

Now from your suggestions, i got new words like, Local repository and so, which now guided me to the right path.

Thanks for that too...

---

