---
title: "Managing a large number of servers"
date: 2012-03-23
forum: Server Platforms
---

### Post by dev.null on 2012-03-23
Greets all.

I'm managing a large number (~80) of ubuntu servers, and the list is growing every day.

My basic complexities are:

1. Servers are in "groups" of two or three that are basically the same, same users, same ubuntu packages, same custom-add-on packages.

2. About 1/2 of all the servers aren't allowed to connect to the Internet. Doing things like 'apt-get update' won't work. I've used 'apt-get --download-only install <package>' to get packages on a "local" machine and then copy them up to those servers and run 'dpkg -i' to keep them updated as needed, but eventually run into problems where a sub-package is required and I have a newer version of it installed (via dpkg -i), but the system doesn't think so.

3. A common /var/usr/local/sbin collection of scripts needs to be maintained on all the servers.

4. All server-specific configs (like /etc/resolv.conf, but not  all of /etc) need to be copied down to a local repository for change management control.

I think you get the basic idea. The thing I'm looking for are recommendations from the community on tools that would help manage this a lot easier. I've looked into things like cfengine and chef, but not convinced either way on which of those are best, and if they'd even work if a server can't connect out to the internet.

Thanks in advance to all who contribute.

---

### Post by devxdev on 2012-03-23
couldnt you run a local SVN on the network?

I think you could some how have a script like updates.sh and be able to get its revision # from SVN, if its -gt $OLD_REV then each server could run the script..?
The only thing you would have to do is just maintain the SVN server with proper files, and update the script. I'm not sure how to fetch files or dpkg of a network interface but im sure it would still be simple/ish.

Edit:
Forgot to say you would also need to run a new cron on all the servers, to check the 'updates.sh' revision number

[How to setup crons]("https://help.ubuntu.com/community/CronHowto")

---

### Post by lykwydchykyn on 2012-03-23
For your non-internet-connected servers, have you considered creating a local repository mirror?  I use one at work, it means my systems can all get updates from a single local system, and it saves a lot of time.

Just google up "apt-mirror" and you should be able to find a tutorial on how to do that.

As for the rest, you might look into [puppet]("http://puppetlabs.com/"), or Ubuntu's (commercial, non-free) Landscape tool.

---

### Post by devxdev on 2012-03-23
> **lykwydchykyn said:**
> Just google up "apt-mirror" and you should be able to find a tutorial on how to do that.


^apt-mirror, NICE! =D>

---

### Post by hawkmage on 2012-03-23
I definitely second the suggestion about creating an internal apt repository.  I would actually go one step further and create two.  One for prod systems and one for non-prod systems.  This way you can easily roll out patches to non-prod systems to test without the chance that prod systems will get them before they have been tested.  

I use a centralized admin system that has all of the info I need to push out to other servers.  I have simple scripts that implement specific functions like updating files or managing processes that are written based on the *nix flavors that I am working with.  Then via key based authentication from my admin system using scp/ssh I copy files and run scripts to do the maintenance.

---

### Post by Habitual on 2012-03-23
dev.null

Check your PMs...

---

### Post by dharmavir on 2012-03-24
As a programmer I see there are few ways:

I agree with earlier comments about using SVN which is a good idea, along with that if that is not possible, you can try anyone from following:
* Use rsync or some similar program written on top of rsync or write your on script to sync programs from one server to rest of the bunch in defined-group.

* You can write a simple web-interface using php/python which can be hosted on one of the management node and that program should give you following functionality:
  - Group server nodes into user defined group/categories.
  - Release program/binaries/scripts on group or individual node.

These are my thoughts, let us know what you finally ended up with?

Are you hosting them on public cloud like amazon or rackspace or your own cloud using vmware or some other virtualization?

---

### Post by SeijiSensei on 2012-03-24
Novell still sells its ZENworks products including [ZENworks Linux Management]("http://www.novell.com/products/zenworks/linuxmanagement/").  The web page says it works on RedHat and SUSE, so I don't know how well it would handle Ubuntu servers.  You might give them a call, though.

---

### Post by lykwydchykyn on 2012-03-24
> **SeijiSensei said:**
> Novell still sells its ZENworks products including [ZENworks Linux Management]("http://www.novell.com/products/zenworks/linuxmanagement/").  The web page says it works on RedHat and SUSE, so I don't know how well it would handle Ubuntu servers.  You might give them a call, though.

I don't know if things have changed since I tried it last year, but I could never get the zenworks agent working on Debian or Ubuntu.

---

### Post by HermanAB on 2012-03-25
A Local Repo and Parallel SSH is what I would use.

---

### Post by collisionystm on 2012-03-25
First I would create one box as the monitoring box. Have it run a script that pings and sends an email if one cannot be reached.

2nd. In your case I would consider even using landscape. I realize its pricey but in your situation it could be the thing you need.

Webmin supports a cluster mode.

Create a central backup station. Have it rsync the files from your servers every night.

You can also setup a program that emails you if your server has any updates available.

These are all the things I have done. (minus landscape) I only have about 15 servers though.

---

