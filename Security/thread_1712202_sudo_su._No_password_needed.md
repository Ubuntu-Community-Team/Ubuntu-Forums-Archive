---
title: "sudo su. No password needed"
date: 2011-03-22
forum: Security
---

### Post by Grafens on 2011-03-22
Can someone explain why when I type sudo su in a terminal there's no need to enter my password, I just go straight into root

Thanks

---

### Post by Tony Flury on 2011-03-22
A few reasons i can think of : 

1) you or someone else has changed your sudoers file to prevent "su" needing a password - sounds an incredibly dangerous thing to do if true.

2) You have recently entered your password in the same terminal as the response to an earlier "sudo" command - in this case sudo remembers your password and does not reprompt.

---

### Post by Grafens on 2011-03-22
Thanks for the quick response. I was doing some terminal stuff but I typed 'exit' when I was finished and presumed that it would completely close the 'sudo permissions bit'.
It seems to be working as it should now.

Thanks Again

---

### Post by sisco311 on 2011-03-22
A little bit off topic, but the preferred method for starting a root shell is **sudo -i**, see: [uhelp]community/RootSudo#Special notes on sudo and shells[/uhelp]

---

### Post by The Cog on 2011-03-22
sudo implements a timer to prevent you having to enter your password repeatedly. It only works for further commands from the same terminal, and I think it is 15 minutes by default. You can kill the timer with the command **sudo -k** .

---

### Post by movieman on 2011-03-23
> **The Cog said:**
> sudo implements a timer to prevent you having to enter your password repeatedly. It only works for further commands from the same terminal, and I think it is 15 minutes by default.

Note that 'same terminal' really means 'same tty device', so if you close one terminal window and then open another, odds are good that the same tty device will be allocated to it, in which case you'll still have the old sudo permissions.

If you want secure sudo then change the timeout to zero so it will ask for the password every time.

---

