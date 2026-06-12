---
title: "Need help with iptables"
date: 2010-11-15
forum: Server Platforms
---

### Post by magix_ch on 2010-11-15
Dear all,

I would like to add a rule in iptables only for 24 or 48 hours.
I found somewhere that it was possible to do this :

iptables -A INPUT -s 1.1.1.1 -j ACCEPT -p TCP --destination-port 22 --datestop 2010:11:15:23:10

but I get :
iptables v1.3.5: Unknown arg `--datestop'

Am I doing something wrong or is there maybe another way to do it ?

Thanks a lot in advance for any help :-))

---

### Post by stlsaint on 2010-11-16
Though i have never used a time for my iptables, it looks like you are missing a pre-command before the --datestop syntax. Try looking at the man page for iptables and or check out a brief tutorial here: [IPtables Primer]("http://bodhizazen.net/Tutorials/iptables/").

---

### Post by magix_ch on 2010-11-16
Ok thank to you advice and man page, I found what was wrong.

I had to do :
 -m time --datestop 2010:11:15:23:10

But now I have another problem :

iptables v1.3.5: Couldn't load match `time':/lib64/iptables/libipt_time.so: cannot open shared object file: No such file or directory

Do you know what I could do (apart from recompiling kernel or iptables) ?

Otherwise I think I will have to add/remove constantly these rules...

Thanks a lot in advance for your help...

---

### Post by SeijiSensei on 2010-11-17
You can always just execute it from a cron job.

---

### Post by magix_ch on 2010-11-17
Yes, but my question, is to identify the rule to be removed. Is there a way to put a comment, or a name to the rule ?

---

### Post by SeijiSensei on 2010-11-17
> **magix_ch said:**
> Yes, but my question, is to identify the rule to be removed. Is there a way to put a comment, or a name to the rule ?

You can identify rules by number, but you really don't need to do that.  Just replicate the entire rule replacing -I or -A with -D.  iptables will then delete the matching rule.

Try it from the command line, and you'll see how it works.

---

### Post by magix_ch on 2010-11-18
Ok it was quite some work to automatize from PHP -> SUDO -> Bash script to add rules based on IP.

But the most difficult was to find a way to remove rules afterwards.

But it works perfectly. Anyone going on the right URL may ask to open the firewall for 24 hours on a specific port, nice for dynamic IPs :-)

Thanks a lot for your advices and suggestions !

---

