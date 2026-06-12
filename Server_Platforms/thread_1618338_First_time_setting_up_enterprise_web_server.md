---
title: "First time setting up enterprise web server"
date: 2010-11-10
forum: Server Platforms
---

### Post by directedition on 2010-11-10
We don't have enough to hire a full-time server admin quite yet (brand new, growing fast), I have been a desktop Linux user for 14 years and have run little servers of my own here and there, but now I'm being asked to spec out hardware and software for a web server that will be fairly high traffic and security and uptime are the two most important variables.

I'm thinking Ubuntu server because I at least know how to setup and administer it. My biggest problem is worrying about uptime. Being that security is a concern, we'll be rolling out patches as fast as they come in, and we'll be restarting the server quite often.

Most solutions I have been proposed involve running two web servers concurrently on an ESX server, and set them up with a round-robin IP based on which is available at a given time (or some facility like that? I have little ESX experience). So when one machine goes down for an update, the other gets its IP and hosts the site till the other one is back up.

Is this a reasonable setup?

---

### Post by SeijiSensei on 2010-11-10
Perhaps so if you're serving static content.  If you're creating dynamic pages with scripts then the real point of failure is the database server.  We had a [discussion]("http://ubuntuforums.org/showthread.php?t=1603251") on this subject recently, and a number of good suggestions were posted.

Web serving is actually a pretty low-impact activity.  I've run Linux web servers for years, and though they don't have very high traffic levels, I've never seen the Apache processes, or my PHP scripts, push the CPU load very high at all.  DB retrievals add some load, but much of that is on the drives.

If you're really concerned about performance you can use one of the various caching/accelerator solutions out there.  That keeps the most commonly-visited pages in memory so disk access is reduced.  

If you're planning on running a PHP site, I'd take a good look at Zend Server; the [community edition]("http://www.zend.com/en/products/server-ce/index") is free.

As for updates, you'll have fewer of those than you might think, and even fewer will require a server reboot.  You only need to reboot when the kernel gets upgraded, which happens very rarely if you're using a stable platform like RedHat/CentOS or Debian  (I don't know whether the same holds true for Ubuntu Server, though.)  Programs like Apache itself will just restart automatically after an upgrade.

---

