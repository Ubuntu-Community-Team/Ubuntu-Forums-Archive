---
title: "Can't get  cron to work"
date: 2009-03-14
forum: Server Platforms
---

### Post by dhimanb on 2009-03-14
I have set up a task for the **root** as /home/tksa/test 

the tksa test file contains
/bin/date >> /home/tksa/test.txt

/home/tksa is the home directory for user tksa. 
However root is the owner and has execute permission for /home/tksa/test

crontab -l gives
35 3 * * * /home/tksa/test

So I expect to get the same time in the test.txt file. But nothing ...
I am using Ubuntu 8.04.2

What am I missing?

---

### Post by sp0nge on 2009-03-14
What seems to be missing is the actual command. 

When using cron, you're scheduling the machine to take some action at the specified time. In doing so, there should be a script called that will execute. 

As a matter of cleanliness (perhaps OCD) I keep all my scripts in /usr/local/bin- this way I know where they are. With this added to the path, I can simply call the script I need for the particular cron job. In addition, I have never run cron without specifying a date.. that may cause issue too. 

Try to create a script, something simple, maybe just the touch command to create another test file. Then you can schedule cron to run your script and all should work.

I Hope this helps.

---

### Post by dhimanb on 2009-03-16
The script file is /home/tksa/test
which has the command

/bin/date >> /home/tksa/test.txt

I created the simple test file (the above script) to check the cron job. 

I have written a job to backup certain directories to a remote location. And I want it to run everyday at 3:35am, when there is only a few users. That is why it doesn't have a date specified.

---

### Post by askreet on 2009-03-16
A few thoughts:

- Check /var/log/messages for when crontab is actually updating itself, maybe it's happening after 3:35.

- Add something like #!/bin/sh to the top of your script.  Depending on a few things, the script may not execute correctly.

Hope this is helpful.

---

### Post by dhimanb on 2009-03-16
Here are the results:

1. I moved the job from 'System' to 'root' (I am using kcron)
.. and it did start working .. any idea why?

2. askreet - Yes.. it did run 5 mins after the time specified.
Why should that be?

Thanks to all who helped.

---

### Post by askreet on 2009-03-17
I'm unfamiliar with kcron, but it seems like unexpected behaviour.

Is anything in the 'System' cron working?

---

### Post by dhimanb on 2009-03-18
No.
This is the first job I was trying to run.

---

