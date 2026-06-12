---
title: "First Time LAMP Installation"
date: 2012-03-30
forum: Server Platforms
---

### Post by Fet600 on 2012-03-30
Hi,

This is probably a fairly dumb newbie question, so please excuse me if this seems obvious.

I'm currently running an Ubuntu desktop installation but I'm looking to get familiar with LAMP set up.  Is it worth installing the seperate packages onto my desktop system or is it just going to cause a lot of headaches that can be avoided by simply wiping it and running a full server installation?

Thanks

---

### Post by agillator on 2012-03-30
I see no problem with installing on the desktop, I do. The server version of Ubuntu is just a different set of software, basically omitting many of the programs a desktop user wants but which are useless on a machine that will rarely, if ever, have a live user using it directly but only of network links.

Anyway, rather than installing the individual programs, the easiest way is to use tasksel. See the writeup here for instructions: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by richardjh on 2012-03-30
I completely agree with [agillator]("http://ubuntuforums.org/member.php?u=1420584"). It'd be different if you were running a production server out in the wilds of the internet but you're not, so enjoy the comforts of running Ubuntu Desktop AND running a LAMP server.

---

### Post by matt_symes on 2012-03-30
Hi

My personal preference is to run LAMP on a headless server. One of the benefits of doing this is that you will learn more in the long run (command line, ssh, iptables etc)

However, as the above two posters quite rightly pointed out, you can just run it on a desktop installation. It's a great way to learn it in an environment (GUI) you are comfortable with.

In the long run though, i suspect you will want a server install.

Less to go wrong. Less overhead (memory, cpu etc). With remote ssh access you can keep it in the loft or basement.

Go with what you feel comfortable with at the moment.

Kind regards

---

### Post by richardjh on 2012-03-30
Your question about whether you can run a LAMP stack on the desktop  install without causing issues is that: yes you can. You don't need to  install a server version especially to do this.
I think Matt's reply highlights the bigger picture in that, if you really want to learn, you should do things properly.

As a best of both worlds, you could install virtualbox which allows you to create virtual machines ( don't worry it is painless ). 
You could then install a ubuntu-server in there as if it were a real production machine. This would allow you to get to grips with the bigger picture of running a LAMP server aside from just the LAMP stack.

Whether you are interested in that at this stage isn't apparent but learning to administer server as Matt suggests is worth it in the long run.

---

### Post by Cheesemill on 2012-03-30
+1 for running a LAMP VM.

A massive advantage with using a VM is that you can take snapshots whenever you wish, if you mess something up it's quick and easy to return the machine to it's last working state.

---

### Post by matt_symes on 2012-03-30
Hi

> **richardjh said:**
> Your question about whether you can run a LAMP stack on the desktop  install without causing issues is that: yes you can. You don't need to  install a server version especially to do this.
I think Matt's reply highlights the bigger picture in that, if you really want to learn, you should do things properly.

As a best of both worlds, you could install virtualbox which allows you to create virtual machines ( don't worry it is painless ). 
You could then install a ubuntu-server in there as if it were a real production machine. This would allow you to get to grips with the bigger picture of running a LAMP server aside from just the LAMP stack.

Whether you are interested in that at this stage isn't apparent but learning to administer server as Matt suggests is worth it in the long run.

Nicely put richardjh :D

@OP. I was not trying to dissuade you from installing on a desktop install. It is a very good way to learn.

I think it depends on what you want to concentrate on (LAMP or the bigger picture) and where you see this going one year down the line.

After all, learning the command line and administration is an extra overhead.

If you want an easier route then richardjh suggestion of virtualisation is an excellent compromise.

If you just want to concentrate on LAMP, install in the desktop.

Isn't it great to have so many choices. Hopefully i have not muddied that waters too much :D

Kind regards

---

### Post by Fet600 on 2012-03-31
Thanks for the suggestions.  Much appreciated.

Since this is my first LAMP installation I think I'll go for the VM option, as this does make a lot of sense and gives me a chance to play about a bit more.  Long term I do plan to switch to server but I expect that I'll use that for a clean install, once I've got all my options figured out.

The fact that there's so many options to get the job done is a real breath of fresh air!

Thanks guys.

---

