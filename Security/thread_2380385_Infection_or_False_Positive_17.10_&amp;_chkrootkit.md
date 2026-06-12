---
title: "Infection or False Positive? 17.10 &amp; chkrootkit"
date: 2017-12-16
forum: Security
---

### Post by pointy2 on 2017-12-16
Lynis (formerly rkhunter) and chkrootkit are installed on 17.10 artful. Lynis came up clean, except for notifying me of potential weaknesses in security, which I am in the process of patching (that will be another thread)

Chkrootkit came back with an "INFECTED" warning. It shows 'tcpd' as INFECTED. Doing a search on the forum as well as google, it shows this as a potential false positive. 

However, when I check tcpd directly with chkrootkit, the output says 'not infected'.

         ```
quasimoto@esmerelda:~$ sudo chkrootkit tcpd
         [sudo] password for quasimoto: 
         ROOTDIR is `/'
         Checking `tcpd'...                                          not infected
         quasimoto@esmerelda:~$ 
```

  
Should I concern myself with the compiled reading? Is there a way to eliminate the false reading from future scans?

---

### Post by deadflowr on 2017-12-16
> Lynis (formerly rkhunter)
Common misconception. Lynis is not a replacement or anything of rkhunter.
They're  different beasts.
They do both share a common author, who explains it well here:
[https://linux-audit.com/tools-compared-rkhunter-vs-lynis/]("https://linux-audit.com/tools-compared-rkhunter-vs-lynis/")

On topic though, yes false positive more likely.
>  Is there a way to eliminate the false reading from future scans?
Not sure, I know you can set a variety of options in rkhunter's rkhunter.conf file, but I do not know if the same is true with chkrootkit.
You can use both if you want by the way.
(Both being rkhunter and chkrootkit)
No harm in using both.

---

### Post by HermanAB on 2017-12-17
In my experience rkhunter and similar tools are not useful.

---

### Post by Habitual on 2017-12-18
rkhunter is what I have relied on.

What does the chkrootkit log file say?
/var/log/chkrootkit.log or similar. Don't, Won't use it here, so IDK  the log file location.

---

### Post by anontrust on 2017-12-19
> **HermanAB said:**
> In my experience rkhunter and similar tools are not useful.

why?

---

### Post by pointy2 on 2017-12-19
> **HermanAB said:**
> In my experience rkhunter and similar tools are not useful.


Why would they not be useful? What isn't useful is the notion that Ubuntu Linux is immune to infection.

---

### Post by Irihapeti on 2017-12-19
In the 10 years that I've been on the forums, I don't recall seeing anyone discovering an infection by using rkhunter or chrootkit. If they're not doing that, and instead provoking a lot of anxiety over false positives, then I can't see how they are useful.

Linux is not immune to infection, but there are more effective ways of preventing that.

---

### Post by HermanAB on 2017-12-20
Well said.  I haven't seen a rootkit since, well, when was it? 2005 on a Windows machine - thanks to Sony.

Rootkits on UNIX machines are simply not a credible threat to waste your time with.  There are better things to do.

---

