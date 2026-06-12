---
title: "How to automatically notify cell phone upon new email received"
date: 2009-11-07
forum: Server Platforms
---

### Post by SpikeBoycom on 2009-11-07
Hi, I'm new to these forums and I'm hoping I've posted this question in the right place.

I've been searching everywhere to try to figure out how to set up my mail server to automatically run a script that can fire off an email to my cell phone to let me know that I have a new email, but I can't seem to find a working solution. It seems as if no one else has this need. Gmail and Yahoo can do it, but I have a dedicated server with cyrus and postfix on it that I want to set up to do this and I can't find any scripts anywhere that will do this for me. I tried setting up a mail handler with postfix but it didn't do anything like it wasn't being run. Here's what I tried. I added this code to the postfix master.cf file:

```

notifycell
          unix  -       n       n       -       -       pipe
  flags=F user=cyrus argv=/usr/bin/perl /usr/bin/notifycell.pl $sender $recipient

```And /usr/bin/notifycell.pl is this:
```

#!/usr/bin/perl
open(FILE,">/tmp/filtertest.txt") || die("can't open file: $!");
print FILE "ARGV0=$ARGV[0]\n";
print FILE "ARGV1=$ARGV[1]\n";
print FILE "ARGV2=$ARGV[2]\n";
close(FILE);

```The script, of course, is just a test script to see if it will run. If it works I'll modify it to check the to address and open sendmail to fire off the email, but for now I just want to get the script to run automatically without stopping the regular email from arriving like it should.

I ran "postfix reload" to reload the master.cf file then emailed myself from a different mail server (gmail) and received the email as usual, but /tmp/filtertest.txt wasn't created. I did "su cyrus" and ran the script from the terminal and it created the file like it was supposed to, so the problem is it's not being run by postfix when a new mail comes in. Does anyone have any suggestions for what I did wrong? Or perhaps someone has already done something like this before and has a tutorial about it? Any pointers would be greatly appreciated.

Thanks,
-Jon

---

