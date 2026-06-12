---
title: "Just instaled Server 12.04 and kinda lost"
date: 2012-05-31
forum: Server Platforms
---

### Post by starz677 on 2012-05-31
Hello,

For Years I've run the Desktop version of ubuntu as servers but now I want to learn to use the REAL server OS for a server instead of the graphical Desktop version.

It's like starting all over again.

Right now all I want to do is configure the server to run a forum.

The LAMP server appears to be working and I can connect to apache2 via local network.

(I'll change /network/Interfaces later back to the settings for serving files to the public but right now I figured it'd be easier to configure and install everything with it connected to my local network as a workstation of sorts)

Anyway, how do I install and use software such as ipblock without any graphical interfaces?  I'm so use3d to watching the graphical output from ipblock that this is going to take a lot of getting used to.

---

### Post by arrrghhh on 2012-05-31
So you're only having issues with ipblock...?

You might want to adjust your thread title accordingly.  You'll have to click 'go advanced' to modify the thread title.

As for a similar package, I've never really looked for one.  Are you wanting something that will help block intrusion into your system?  I like fail2ban myself, but I don't know if that's exactly what you're looking for.

You must keep in mind that a lot of the GUI tools utilize CLI tools in the back-end - the GUI is just a nice way of displaying the information to the end-user.  So most tools you are used to need to be broken down into components, and then you can just utilize the components.  Or, find another package entirely that better suits your needs :).

Remember, the CLI isn't the be-all, end-all solution for everyone.  I really like it because I prefer remote administration, and web interfaces are plenty for me.  For your application, it might not work and perhaps Ubuntu Desktop is a better solution.  After all, you can run all the same services on Ubuntu Desktop that you can on the Server edition - it's just the Server edition is very stripped so it runs with the least possible resource footprint, and the least pain as far as upgrades go (less packages to update/fail/etc).

Edit - with all that said, a quick google search turned up [this](http://www.the-little-things.net/blog/2009/11/21/107/).  Hopefully it's helpful.

---

