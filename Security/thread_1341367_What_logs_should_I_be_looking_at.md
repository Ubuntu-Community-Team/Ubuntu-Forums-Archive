---
title: "What logs should I be looking at?"
date: 2009-11-29
forum: Security
---

### Post by mr-woof on 2009-11-29
Hi all,

I've been using Ubuntu about a year or so now, I've been browsing this section of the forums quite a lot lately and I've realised I don't know how to check what's running on my system. what logs I should be looking at on a regular basis etc etc

Now, I've got no ports open, nothing getting forwarded. 

1) How do I check what's running?
2) What logs should I/do you check on a day to day basis?

I'm used to windows, checking the event logs, running processes, IIS logs, running virus scans etc :(

Thanks for any info :)

---

### Post by rookcifer on 2009-11-29
> **mr-woof said:**
> Hi all,

I've been using Ubuntu about a year or so now, I've been browsing this section of the forums quite a lot lately and I've realised I don't know how to check what's running on my system. what logs I should be looking at on a regular basis etc etc

Now, I've got no ports open, nothing getting forwarded. 

1) How do I check what's running?
2) What logs should I/do you check on a day to day basis?

I'm used to windows, checking the event logs, running processes, IIS logs, running virus scans etc :(

Thanks for any info :)

To list all running processes:

```
ps -A
```

To watch them in real time:

```
ps aux | less
```

You can also use "top" but it will not list every single process, only those that are active:

```
top
```

Top has various options you can pass to it.  So just read its man page.  Also read the "ps" man page.

As for logs, do you have logwatch installed?  If not, just install it and it will give you a list of interesting logs when they become available.  It is highly configurable.

Also you can look into intrustion detection systems such as AIDE.  Or you can look into SNORT (which I think is way overkill for a desktop machine).  

Of course, you also have the logs in /var/log

---

### Post by tubbygweilo on 2009-11-29
mr-woof,
> Now, I've got no ports open, nothing getting forwarded.
 and you are up to date with Ubuntu security updates then unless you have compelling grounds for suspecting you have been compromised you have little need to view your logs. All in all Ubuntu is quite secure with the default settings but if worried then by all means examine your various logs and seek advice as you are doing.

---

### Post by mr-woof on 2009-11-30
yes running 9.04 with all updates complete at the moment. Ok, say I install ssh and ran that with port forwarding to this machine, what logs should I be looking at? 

How would i secure ssh?

---

### Post by XCan on 2009-11-30
-Change the ssh port (this by itself will eliminate almost all bot attacks). 

-Set it up to only be able to login using keyfiles (there are several threads here discussing how to do that). 

-Install fail2ban to automatically drop bruteforcers (this is more optional tbh if you used the above steps).

For logs, check auth.log. It will list all login attempts.

---

### Post by kpholmes on 2009-11-30
go to /var/log/


auth.log - authorization log, if you/someone ssh's into your pc then you'll see it there

and proftpd, if you have proftpd installed. 

you can lock down ssh with RSA keys, theres plenty of tutorials on how to install them, i dont have them installed cause im lazy. 


a couple of techniques you can use to lock down ssh is try running it on a nonstandard port. running ssh or any service on a nonstandard port will just help prevent from bots scanning that port accross a range of ip addresses. its not going to protect you from a hacker trying to break into your machine. 

just use RSA keys or make a really safe password.

[http://www.passwordmeter.com/](http://www.passwordmeter.com/)

---

### Post by kpholmes on 2009-11-30
> **XCan said:**
> -Change the ssh port (this by itself will eliminate almost all bot attacks). 

-Set it up to only be able to login using keyfiles (there are several threads here discussing how to do that). 

-Install fail2ban to automatically drop bruteforcers (this is more optional tbh if you used the above steps).

For logs, check auth.log. It will list all login attempts.

you beat me to it, by seconds. haha.

---

### Post by BkkBonanza on 2009-11-30
I generally like to look at a few thinngs. 

For current process I use either "ps -afx" which gives a nice tree view and all processes, or I use htop (which is in Synaptics but not installed by default). It's a nicer version of top.

For ports/connections I use "netstat -lntp" to show any ports listening, or "netstat -ntp" to list the connections open currently.

I like to browse a few of my logs from time to time and get an idea of what is normal there so that things later may stand out. Also sometimes you find errors that need fixing.

/var/log/messages
/var/log/auth.log

I usually look at my web server logs in there too and a few others. Sometimes having a look through your boot.log can be interesting. It's the auth.log that contains messages about users logging in but be aware that if someone does get in and achieve root they can doctor your logs to hide any trail they would have left. They can install a rootkit that would hide any current activity. I run chkrootkit in a cronjob everyday but I'm not sure how effective that really is. Best is preventative security as suggested by some above and various other standard security sticky posts here.

---

### Post by EJeanmaire on 2009-11-30
```
lastb
```

This command will show you failed login attempts.

---

