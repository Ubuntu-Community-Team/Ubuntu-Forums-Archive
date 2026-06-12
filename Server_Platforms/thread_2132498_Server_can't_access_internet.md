---
title: "Server can't access internet"
date: 2013-04-05
forum: Server Platforms
---

### Post by anonkage on 2013-04-05
So I have Ubuntu Server running on a machine but I can't access the internet with it. I have it hooked up through an ethernet cable, but I am at a university and they require you to sign in through a web browser before accessing the internet. I can't go in because it will only recognize the browsers like chrome, firefox, ie, etc. I tried using a command line browser and didn't get anything. Anybody here have a solution for this? I can't install firefox because of the lack of internet access. I'm not able to install it over SSH, because the connection fails now, even though it was working earlier. This happened after running updates (apt-get upgrade) and then rebooting. Any input is greatly appreciated, I've been working at this for a while without any progress.

---

### Post by anonkage on 2013-04-05
This is a repost from Networking help, but I'm new to the forums and wasn't sure on how to move the thread.

So I have Ubuntu Server running on a machine but I can't access the  internet with it. I have it hooked up through an ethernet cable, but I  am at a university and they require you to sign in through a web browser  before accessing the internet. I can't go in because it will only  recognize the browsers like chrome, firefox, ie, etc. I tried using a  command line browser and didn't get anything. Anybody here have a  solution for this? I can't install firefox because of the lack of  internet access. I'm not able to install it over SSH, because the  connection fails now, even though it was working earlier. This happened  after running updates (apt-get upgrade) and then rebooting. Any input is  greatly appreciated, I've been working at this for a while without any  progress.

---

### Post by lvlint67 on 2013-04-05
I was a student and currently work at a college. I believe the general procedure is to contact the college HelpDesk and request that the servers Mac address be whitelisted.

You will likely need to provide a reasonable explanation for the request.
_________
You MIGHT be able to work around this by adding a second 'local' nic, connecting a working PC and using an ssh tunnel to authenticate.... You will surely be violating the campus network policy and are likely to get banned for such endeavors
_______
.... I have done this type of thing with a headless virtual box install and some internal network voodoo... See: ICS....
______
The easiest way is to just get the Mac address bypassed. You clearly need a headless Linux box for a program you are writing for one of your classes... Good luck..

---

### Post by anonkage on 2013-04-05
Alright I'll have to give that a shot in the morning. Continuing to try to figure this out tonight is quite likely dangerous to my blood pressure. Thanks for the help!

---

### Post by darkod on 2013-04-05
Can't the IT department at the Uni help you out? They usually have these limitations for a reason. If you are allowed to do this, they can probably configure an exception for the server machine so you can configure internet in the standard way without web login.

I'm not sure if someone here can help you, personally I've never had to configure internet on a server with such limitations.

---

### Post by lisati on 2013-04-05
Threads merged. Please do not start multiple threads, it dilutes the community's ability to help.

If you want help moving a thread, the forum staff won't mind if you use the "Report" button to ask for your thread to be moved.

---

### Post by oldschoolgentoo on 2013-04-05
Most Uniy's  IT departments will with a bit of asking should give you access to a separate system that has a gateway out into the web for Class use.   Its a request that they should give you access,  I am assuming you only have a stand alone that is not trying to access their internal network at the same time?   Just a box that needs internet access?

IT Guys are just like you  just a bit further in their studies and a few creds to their name.

---

