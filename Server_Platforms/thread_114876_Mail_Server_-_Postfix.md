---
title: "Mail Server - Postfix"
date: 2006-01-09
forum: Server Platforms
---

### Post by Wolfmann on 2006-01-09
Is there anyway to have postfix sniff all SMTP traffic directed at it, and as each e-mail comes in to store it in one directory as basically a temporary file so a white/black list perl script can read it, determine if it's deliverable, and then either return the e-mail to pass it off to the e-mail server? 

Basically, we want PostFIX to take all mail traffic and save it into one folder, not multiple one's, or not differentiate it by account.

---

### Post by LordHunter317 on 2006-01-09
You need to explain what you're trying to accomplish further, because whatever you're really trying to do, that's assuredly the wrong way to do it.

---

### Post by Wolfmann on 2006-01-09
I work for an IT consulting company, and while there are probably better ways to do it...let me know...but we have specific requirements in our sub-systems that may not be under our control. 

Basically, we are running a Netware e-mail server that is running Mercury and a white/black list Perl script. We want to migrate our front end services to linux and to support our current services for our client we want to be able to receive SMTP traffic, store it all in a single folder and then have the black list script interrogate the traffic, append some information to the e-mail, and either send it back with a polite message "Get on our white list or your e-mail will continue to be dropped" or will then deliver it to the backend netware servers.

I'm tasked with making that requirement happen, not necessarily re-designing the entire strategy...BUT...if you can think of a better way, I'm all ears.  

I've considerrf piping with SMTPD as well, but honestly we don't know much about Linux, and I'm the one that's basically being paid to learn it. This is part of an ongoing project, and our current system is working...we just want to use linux on the front end side, instead of Netware.

---

### Post by Wolfmann on 2006-01-11
Am I to understand, that of all the super Linux guru's in this world, none of them can intelligently help me?

We're also interested in possibly piping SMTP traffic from the SMTPD process to create files in a specific directory. Each e-mail has to be its own file anyway, all we need is one spot for this perl script to interrogate the mail.

---

### Post by Soleil-Raid on 2006-01-11
I'm not very familier with Postfix, but I'd imagine there's stuff in it that lets you hand off the email, or parts of the content to a perl script, and depending on what that perl script returns, do various things to the email (such as drop/bounce/allow, etc).

---

