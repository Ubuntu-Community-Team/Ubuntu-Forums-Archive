---
title: "Newbie: timeout in crypttab being ignored"
date: 2010-07-15
forum: Security
---

### Post by supremedalek on 2010-07-15
Quick and easy question: I have in my /etc/crypttab something like this:

```
funkydevice     /dev/sda5 none            luks,timeout=30
```

I tell the machine to reboot and it asks as it should for the password. Waiting to see if it will timeout for 30 seconds, I do not type the password. And wait and wait and wait. And nothing happens. Am I missing something here?

---

### Post by cariboo on 2010-07-15
What is it that you expect to happen after the 30 second time-out?

---

### Post by supremedalek on 2010-07-15
I was hoping something on the lines of > The timeout option specifies the time in seconds to wait for the password before timing outWhat would it do after that timeout expires? Does it tell no password/passphrase was entered and then prompts for a new one or just waits for user intervention?

---

### Post by viralmeme on 2010-07-15
> **cariboo907 said:**
> What is it that you expect to happen after the 30 second time-out?

Maybe this is what he is referring to ..

> You will be prompted for the password at boot. In this example we have set a maximum of 3 attempts per reboot, and an automatic timeout on password entry after 60 seconds. That's important if you access your system over a network and don't have physical access.[http://besy.co.uk/debian/how_to_setup_file_system_encryption_with_dm-crypt](http://besy.co.uk/debian/how_to_setup_file_system_encryption_with_dm-crypt)

---

### Post by supremedalek on 2010-07-15
viralmeme, that is exactly what I had in mind. :D I know how to do that is quite obvious for most here, but it baffles me. I have tries=5 and timeout=20 and I can walk away from the machine and come back in an hour and it would still be patiently waiting for the passphrase. This is a fresh install of 10.04 LTS if that matters.

One thing I noticed is that timeout is not mentioned in the man page for crypttab in my 10.04 LTS install, but it is mentioned in [http://manpages.ubuntu.com/manpages/hardy/man5/crypttab.5.html](http://manpages.ubuntu.com/manpages/hardy/man5/crypttab.5.html). Could it have been deprecated/removed?

---

### Post by chaitatp on 2012-09-15
I am having the same problem. "timeout" option doesn't seem to work.

Debian 6.0

---

### Post by overdrank on 2012-09-15
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

