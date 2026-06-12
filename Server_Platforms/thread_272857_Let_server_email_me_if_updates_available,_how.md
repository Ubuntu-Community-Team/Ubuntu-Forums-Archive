---
title: "Let server email me if updates available, how?"
date: 2006-10-07
forum: Server Platforms
---

### Post by Jingo on 2006-10-07
I'm setting up a Ubuntu LAMP server.

Maintanence is easy using apt-get etc. But how do I set up a cron job who sends me an email listing the updates available from the repositories ?

This would be nice, so I don't have to login to the server and check if updates available. I might not be interested in every update!

And as a sidenote: What info are you collecting from the server ? Did you set it up to email you with resumés of the log-files ? how ?

Thanks.

/Jingo

---

### Post by paul.maddox on 2006-10-07
Very good idea!

I'd be interested in this, might even write a script for it if I get bored next week.

---

### Post by Jingo on 2006-10-07
> **paul.maddox said:**
> Very good idea!

I'd be interested in this, might even write a script for it if I get bored next week.

So you're saying, this is not a standard feature!! I just thought my search skills had degraded.

I hope you'll post you solution here.

What would be the basics of the script.

```

apt-get update
$EMAILMSG = `apt-get give-me-a-list-of-updates`
send ($EMAILMSG)

```

How do I assemble the list without asking for installation?
Hmm... I really should spend some more time dating "apt"

---

### Post by paul.maddox on 2006-10-07
I've no idea if the functionality exists already but I spent a little time writing a BASH script to do it. 

To install the script:

```

paul.maddox@web1:~$ sudo wget -O /usr/bin/check-updates http://support.office-shadow.com/check-updates
paul.maddox@web1:~$ sudo chmod +x /usr/bin/check-updates

```

It depends on sendmail to send emails at the moment. If you don't have sendmail installed it will fail
```

paul.maddox@web1:~$ sudo apt-get -y install sendmail

```

To run the script:
```

paul.maddox@web1:~$ sudo check-updates

```


Ideally it'd be put in a cron job to run on a daily basis.

The only issue I have with the script at the moment is that if you don't install the updates when it emails you, it'll email you about them again the next day. It has no memory of what it's already emailed.

---

### Post by paul.maddox on 2006-10-07
Sorry, I forgot to mention...

You'll want to change the email address it sends to

If you open up the check-updates file, there are some configuration variables near the top

You'll want to change the EMAIL="..." variable to contain your email address

---

### Post by Jingo on 2006-10-08
Very great.

I will look into your script and update for my needs.

Thanks a lot.

I think you should put this available on your website, others might be interrested.

Exactly what I was looking for. ;-)

---

