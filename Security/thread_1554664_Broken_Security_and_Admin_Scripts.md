---
title: "Broken Security and Admin Scripts"
date: 2010-08-17
forum: Security
---

### Post by sTpny on 2010-08-17
Hi everyone, 

I babysit (administrate) a bunch of Linux computers locally, but now I'm moving away, so rather than leave everyone stranded, I'd like to instead get everyone set up for remote administration, so I can still fix things for them after I move. I've copied/built some scripts to help set this up, but so far, it isn't working, and my scripting skills, like my admin skills, are still minimal, and I can't figure it out.  Everything seems to be working except the part that emails their info to me (current ip, security logs). Could someone with some more skill that I have take a look, and see if they can figure it out.  There is more info about the scripts in the README.  

[http://ubuntuone.com/p/Cxd/](http://ubuntuone.com/p/Cxd/)   <-- Broken Security and Admin Scripts. 

I'll be publishing the working script too.. so everyone that needs/wants to can use it. 
 
Thanks 

Tony. 

Afterthought:  Might it be easier to use Ubuntu One rather than email.. ? Can a script be used to setup Ubuntu One for this.. assuming it isn't already set up.. ? Just me thinking out loud.

---

### Post by HermanAB on 2010-08-17
Hmm, set up sshd on each machine on a non-standard port, e.g. 2222 (to defeat script kiddies) and forward port 2222/TCP to the machine in the internet router.  Test ssh access properly.

When someone needs support, ask them to run Firefox and go to [http://whatismyip.com](http://whatismyip.com) and read it to you.

---

### Post by CharlesA on 2010-08-17
The one thing that stands out is that you included ssh_config not sshd_config.

I'll take a look at the other scripts and let you know.

---

### Post by FuturePilot on 2010-08-17
One thing that stands out is that in remote_admin_setup.sh you're modifying ssh_config when you want to be modifying sshd_config.

---

### Post by koenn on 2010-08-17
the errors indicate you specified a file named "--"", which doesn't exist.
i guess this comes from your 'email' command
```
mutt -s "$subject" -a $attach -- $to < /dev/null 
```
you may want to check man mutt for correct syntax

also, have you checked that the substitution ```
sed 's/your@email.addr/$1/g' 
``` actually works ? AFAIK, single quotes make literal strings, so you might not get the value of $1; possibly this results in an incorrect command line for mutt later on when you try to give it its to-address.

---

### Post by sTpny on 2010-08-24
> **CharlesA said:**
> The one thing that stands out is that you included ssh_config not sshd_config.

I'll take a look at the other scripts and let you know.
Oops.. that would be a problem. Thanks for pointing it out.

---

### Post by sTpny on 2010-08-24
> **CharlesA said:**
> The one thing that stands out is that you included ssh_config not sshd_config.

I'll take a look at the other scripts and let you know.
Much appreciated.. Thanks.

---

### Post by sTpny on 2010-08-24
> **FuturePilot said:**
> One thing that stands out is that in remote_admin_setup.sh you're modifying ssh_config when you want to be modifying sshd_config.
Thanks for the good eye.. I'll change it right away.

---

### Post by sTpny on 2010-08-24
> **koenn said:**
> the errors indicate you specified a file named "--"", which doesn't exist.
i guess this comes from your 'email' command
```
mutt -s "$subject" -a $attach -- $to < /dev/null 
```
you may want to check man mutt for correct syntax

also, have you checked that the substitution ```
sed 's/your@email.addr/$1/g' 
``` actually works ? AFAIK, single quotes make literal strings, so you might not get the value of $1; possibly this results in an incorrect command line for mutt later on when you try to give it its to-address.
Thanks.. I think you may have found the cause of the major error.  If the email address is wrong, the mutt command wouldn't work.  Looks like I have some editing/testing to do. :)

---

### Post by sTpny on 2010-08-24
Yes.. you were right.. my sed command is creating email=$1.. Thanks again.

---

