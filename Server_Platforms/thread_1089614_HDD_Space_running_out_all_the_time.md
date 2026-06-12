---
title: "HDD Space running out all the time"
date: 2009-03-07
forum: Server Platforms
---

### Post by cyphunk on 2009-03-07
Hi,

I have a server running Ubuntu Server 8.04. The server has a 40GB hard drive (37GB partition visible in df -h results)

The server is used as a gateway and runs squid. The machine also uses Fetchmail to pick up mail from a POP3 server and distribute it to users on the machine/network.

The server is running LOW on diskspace. I have to delete logs, clear Squid Cache, delete users mail, delete unused programs, etc every day to try prevent the disk from running out of space. Now I am at the point where in the last 5 days I was able to free up 200mb space every day. Today (Saturday) I cleared 450MB of space and 4 hours later I am down to 370MB. I am at my wits end as I am not sure what to delete next :P

By Monday morning the machine will be out of disk space again and services will stop functioning again.

As far as I am concerned the server shouldnt take up 37GB on operating system files. What can I do to clear up a mass of disk space?

Thanks in advance for any help that you can give me.

Chris

---

### Post by miegiel on 2009-03-07
40GB should be enough. Empty trash, look for junk in the home directories and check squid caching setting (don't let it cache more than 20GB).

---

### Post by hictio on 2009-03-07
Does the server have any other user besides yours? I mean, for instance, shell accounts .
It is only being used as an internet (?) gateway & Squid, right?

Does one of the network interfaces faces (doh! :) ) the internet? Do you have any service available that can be reached that way?

How did you partitoned your server's HDD? Is it just one partition on / (and swap)?

You have issued a df -h, but, you should, also, run this to see which directory/ partition it is actually using more HDD.

```

cd /
sudo du -sh *

```

Like miegiel says, take a look at the Squid config file '/etc/squid/squid.conf' specifically the  "cache_dir" directive.

---

