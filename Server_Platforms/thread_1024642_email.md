---
title: "email"
date: 2008-12-29
forum: Server Platforms
---

### Post by mregister on 2008-12-29
Hello All,

I need to setup email so that a php script can send email to various departments in our company. We do not have internal email and connect to a ISP for email using the standard pop and smtp setup. I am running a LAMP setup under Hardy and this box is a webserver so I don't need to recieve emails neccessarly just send them. and sending the admin reports would be nice to. I have played around with Exim4 but I must be missing something or setting up incorrectly. Any advice?

Thanks to all,

Mark

---

### Post by jamesrfla on 2008-12-29
I use Citadel. It is easy to set up and use. It also shows you what e-mails are being sent at that moment.

---

### Post by mregister on 2008-12-29
So would i need to uninstall exim4 first?

---

### Post by jamesrfla on 2008-12-29
You can keep both on at the same time if you want. When you do finally decide which one you want uninstall the others then.

---

### Post by albinootje on 2008-12-29
> **mregister said:**
>  I need to setup email so that a php script can send email to various departments in our company. 
I recommend replacing exim4 by either postfix or ssmtp if you only need to send out emails.

Ssmtp should be the easiest, it has one short config file and one alias file after installation : 
```

sudo apt-get install ssmtp

```
Look in /etc/ssmtp/ after installation.

Default /etc/ssmtp/ssmtp.conf :

#
# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=postmaster

# The place where the mail goes. The actual machine name is required no
# MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=mail

# Where will the mail seem to come from?
#rewriteDomain=

# The full hostname
hostname=ubuntu-desktop

# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
#FromLineOverride=YES

---

### Post by mregister on 2008-12-29
Thanks for that. Looking at the config file I am still confused on one issue. My email provider is an ISP. How do I get my server to send out the messages? Like on my windows client, i have to have an account that I login with to send and receive emails.

---

### Post by albinootje on 2008-12-29
> **mregister said:**
> Thanks for that. Looking at the config file I am still confused on one issue. My email provider is an ISP. How do I get my server to send out the messages? Like on my windows client, i have to have an account that I login with to send and receive emails.

Here's two howtos for using a username and password with ssmtp :

[http://blogs.techrepublic.com.com/security/?p=440](http://blogs.techrepublic.com.com/security/?p=440)
[http://www.linux.com/feature/132006?theme=print](http://www.linux.com/feature/132006?theme=print)

See also : man ssmtp

---

### Post by mregister on 2008-12-29
Ok it looks like that will work for me. Thanks albinootje.

---

### Post by MJN on 2008-12-29
If you only require outgoing e-mail then I would recommend looking at Nullmailer. The forum archives are full of examples/discussions of its use.
 
Mathew

---

### Post by CrucifiedEgo on 2008-12-29
or if you stick with ssmtp -- i'd recommend switching to msmtp.  ssmtp seems to be abandoned and i think msmtp is either based on the same code, or written to be nearly identical.

---

### Post by mregister on 2008-12-30
sheesh, it looks like I may stick with exim4, nothing else seems to want to install. Thanks to all of  you for  your input.

---

### Post by albinootje on 2008-12-30
> **mregister said:**
> sheesh, it looks like I may stick with exim4, nothing else seems to want to install. Thanks to all of  you for  your input.

That's weird.
Can you show us any errors ?
Did you install software before on that machine in the current situation ?
Or did you do the install at home and then you took the hard disk to your work machine ?

---

### Post by linux_tech on 2008-12-30
exim is faster because of not relying on queueing

---

### Post by mregister on 2008-12-30
> That's weird.
Can you show us any errors ?
Did you install software before on that machine in the current situation ?
Or did you do the install at home and then you took the hard disk to your work machine ? 

When trying to install ssmtp I get conflicts with mail transfer agent. I had to stop and work on something else for awhile but after thinking about it I am going to work exim4 and try to get it to work as it seems I will learn alot about mail in the process. I have noticed that since I have been messing around I don't get local/user email from cron jobs or anything and I can't send when running ```
mail mark@whatever.com
```

---

### Post by albinootje on 2008-12-30
> **mregister said:**
> When trying to install ssmtp I get conflicts with mail transfer agent. I had to stop and work on something else for awhile but after thinking about it I am going to work exim4 and try to get it to work as it seems I will learn alot about mail in the process. I have noticed that since I have been messing around I don't get local/user email from cron jobs or anything and I can't send when running ```
mail mark@whatever.com
```

It's up to you, and I can understand now that you need more than just a "nullmailer". 

But again, for me personally Exim4 is like Sendmail, way too complex to handle.
Postfix is so much easier, it's almost unbelievable.

GL!

---

