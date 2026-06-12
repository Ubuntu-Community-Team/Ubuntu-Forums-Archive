---
title: "Get mail notification on SSH logins"
date: 2007-10-31
forum: Server Platforms
---

### Post by globemast on 2007-10-31
Hello all,

i found a [HERE]("http://www.crucialp.com/resources/tutorials/secure-server-securing/email-alert-root-ssh-login-e-mail.php") small script which you can include in the .bashrc file and you get notified via email when root logins to a machine.

Is there any centralized way to have such a script as the one above so that i can get notified when any of the users login to a machine? not just root?

Thanks.

---

### Post by Vixis on 2007-10-31
For systemwide functions edit /etc/bash.bashrc
For one user edit $HOME/.bashrc

---

### Post by globemast on 2007-10-31
Thanks for the prompt reply.

Be the way? Do you know which any command line mail application that i can use in Ubuntu?

I have tried "mail" but it does not work for me.

Thanks.

---

### Post by MJN on 2007-10-31
Install the **mailx** package - the mail binary is in there (you'll also find one in **mailutils** but if you don't need all the extra stuff...).
 
Mathew

---

### Post by globemast on 2007-10-31
Hi MJN,

i have the mail binary installed but the problem is that i cannot send mail with it.

If i do for example:
```
 mail -s "HI" myemail@domain.com 
```

it freezes and returns nothing. 

Any suggestions? Is there any config file for it?

Thanks,

---

### Post by MJN on 2007-10-31
It's expecting the message body from standard input i.e. you typing it in (before hitting ^D to end the message - see the man page) - that's what it's waiting for.
 
Given you're using mail in scripts you'll want to do one of the following:
 
```

# Send simple message by e-mail
echo "Simple message." |mail -s "Test" [EMAIL="myemail@domain.com"]myemail@domain.com[/EMAIL]
 
# Send a longer message by e-mail
mail -s "Test" [EMAIL="myemail@domain.com"]myemail@domain.com[/EMAIL] < filewithtext.txt
 
# Send the output of a command
echo "`df -h`" |mail -s "Test" [EMAIL="myemail@domain.com"]myemail@domain.com[/EMAIL]
```
 
Any help?
 
Mathew

---

### Post by globemast on 2007-10-31
From what i've read i need to run Exim in order to user "mail"

Do you know how to setup Exim ? I need to specify my SMTP mail server.

---

### Post by MJN on 2007-10-31
You do need an MTA, but it doesn't have to be Exim.
 
Install Postfix and you should be up-and-running straight away. It is secure by default so even if you don't use it (other than for delivering local mail) it's not going to cause you any problems. Exim may well work out of the box too but I've never used it.
 
Mathew

---

### Post by globemast on 2007-11-01
Hi MJN,

thanks. i installed postfix and with a simple configuration i was able to send mail from the command line. 

The problem now, is that i have included the above script in my bash.bashrc file in order to monitor SSH logins but i receive alerts also when i open my terminal window :P

Any suggestions on how to avoid getting the alert when opening the terminal window?

Thanks,

---

### Post by MJN on 2007-11-01
I'm afraid not, although I do see that you would get an alert whenever any shell is started, regardless of whether it was done via SSH (I'm surprised the original author didn't recognise this).
 
Perhaps there is some means for a script to determine what terminal the shell is attached to but I will have to leave that to someone else to solve.
 
Mathew

---

