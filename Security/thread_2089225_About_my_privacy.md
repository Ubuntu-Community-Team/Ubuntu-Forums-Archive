---
title: "About my privacy"
date: 2012-11-28
forum: Security
---

### Post by maodogo on 2012-11-28
Hi all,

How can i be sure that i am not being tracked by de engine or whatever that come with in Unity Lens, Amazon lens, etc, etc.

I am worried about it.

A mean, which tool can i use for that purpose, for watching the open ports, etc.


Note: I did puge on amazon-lens, and switch off the annoying option of "Record Activity" in the System Settings.
  
Thnx!

---

### Post by houseworkshy on 2012-11-28
The easiest thing to do is get rid of it.  "sudo apt-get remove unity-lens-shopping" entered in the terminal will do that.  
As to tracking in general there are some good add-ons for firefox; "better privacy" lets you get rid of the lso's which are a sort of never expiring super cookie and "no-script" blocks a lot of unwanted java.
 
There is some good stuff in the default repositories which you could install via "sudo apt-get install" or via any of the graphic installers. 
Wireshark is a handy program to see what is going on with your machine's network.  If you think your machine has been compromised you could install and run "rkhunter" to check for rootkits.  Once in "man rkhunter" will give you details.
On a fresh Ubuntu  installation there is a firewall included, ufw,  you can see whether or not it is active with "sudo ufw status" but it won't be running unless you have told it to.   So "sudo ufw default deny" sets up decent defaults, then "sudo ufw enable" starts it running and will also initialise it on future bootups.  If you want to fine tune the firewall you can find details in its manual page with "man ufw".

---

### Post by maodogo on 2012-11-29
Ok i understand thanx for the reply.

But i tried to say my trust on a Ubuntu´s fresh install is gone
because the inclusion of Amazon Lens and all those staff in Unity webapp "integration".

Before created this Thread i purge that trash, but is sad, didn´t feel
that paranoid in linux as in Windows. But with 12.10 im feeling same.

Bad for me.

---

### Post by snowpine on 2012-11-29
Here is Mark Shuttleworth's (supreme leader of Ubuntu) response to this topic:

[http://www.markshuttleworth.com/archives/1182](http://www.markshuttleworth.com/archives/1182)

My favorite part:

> Chill out.

---

