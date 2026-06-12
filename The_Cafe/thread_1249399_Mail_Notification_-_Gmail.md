---
title: "Mail Notification - Gmail"
date: 2009-08-25
forum: The Cafe
---

### Post by Buschbarber on 2009-08-25
I use Gmail as my email client. I found that the Gmail Screenlet was a convenient way to keep me updated as to how many new messages had arrived in my Gmail Inbox.

Unfortunately, the Gmail Screenlet does not provide an Audible Notification.

I came across a program called Mail Notification, It sits in the System Tray and notifies me both Visually and Audibly when new messages arrive.

The problem is, when I click on the Mail Notification Status Icon, it launches Evolution (which apparently the default email client).

I found a procedure to make Gmail my default email client, for Ubuntu, but when I click on the Mail Notification Status Icon, it launches Compose a Message instead of opening my Gmail Inbox.

Any ideas on how to correct this?

---

### Post by Tibuda on 2009-08-25
How have you made Gmail your default email client? This is the script I use, and it works fine with mail-notification. It opens the inbox if there are no arguments, and a compose message dialog if there is an argument.
```
#!/bin/bash
if [ "$1" = "" ]; then
  URL="https://mail.google.com/mail#inbox"
else
  RCPT=`echo "$1" | sed -e 's/subject=/su=/' -e 's/^mailto:\([^&?]\+\)[?&]\?\(.*\)$/\1\&\2/'`
  URL="https://mail.google.com/mail?view=cm&tf=0&to=$RCPT"
fi
echo $URL
x-www-browser "$URL"
```

---

### Post by matthewbpt on 2009-08-25
I install a package called 'checkgmail'. It also resides in your system tray and checks your gmail account automatically, and when you hover your mouse over it you can see what the emails are and even read them if you like, and if you click on the icon it will open your gmail in firefox (or another browser of your choice). In the configuration it also has a field for 'Launch command when mail is received' and I put the following in there 'paplay /path/to/sound/file', choosing an appropriate sound file, and now whenever I receive mail I get a sound notification, very handy.

---

### Post by Buschbarber on 2009-08-26
> **danielrmt said:**
> How have you made Gmail your default email client? This is the script I use, and it works fine with mail-notification. It opens the inbox if there are no arguments, and a compose message dialog if there is an argument.
```
#!/bin/bash
if [ "$1" = "" ]; then
  URL="https://mail.google.com/mail#inbox"
else
  RCPT=`echo "$1" | sed -e 's/subject=/su=/' -e 's/^mailto:\([^&?]\+\)[?&]\?\(.*\)$/\1\&\2/'`
  URL="https://mail.google.com/mail?view=cm&tf=0&to=$RCPT"
fi
echo $URL
x-www-browser "$URL"
```

I am not too familiar with how to handle Scripts. What are the steps I need to take to use this Script?

---

### Post by Buschbarber on 2009-08-26
> **danielrmt said:**
> How have you made Gmail your default email client? This is the script I use, and it works fine with mail-notification. It opens the inbox if there are no arguments, and a compose message dialog if there is an argument.
```
#!/bin/bash
if [ "$1" = "" ]; then
  URL="https://mail.google.com/mail#inbox"
else
  RCPT=`echo "$1" | sed -e 's/subject=/su=/' -e 's/^mailto:\([^&?]\+\)[?&]\?\(.*\)$/\1\&\2/'`
  URL="https://mail.google.com/mail?view=cm&tf=0&to=$RCPT"
fi
echo $URL
x-www-browser "$URL"
```

This is the procedure I followed to make Gmail the default mail client:

[http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/)

---

### Post by Tibuda on 2009-08-26
> **Buschbarber said:**
> This is the procedure I followed to make Gmail the default mail client:

[http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/)

Just replace the open_mailto.sh contents with the script I posted.

---

### Post by RabbitWho on 2009-08-26
there's an ad on for firefox that checks your gmail every five minutes and you can tell it to make a sound in the settings if you like. 

there are two I think, but the one i use is the one that says it's the original.

---

### Post by Buschbarber on 2009-08-26
> **Buschbarber said:**
> This is the procedure I followed to make Gmail the default mail client:

[http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/)

Your script worked fine except it connects to Gmail through Konquerer instead of Firefox. How do I change that?

---

### Post by Tibuda on 2009-08-26
> **Buschbarber said:**
> Your script worked fine except it connects to Gmail through Konquerer instead of Firefox. How do I change that?

I suppose you are using KDE? The best way would be setup Firefox to be your main browser. I can't help you with that in KDE. Other way is to replace **x-www-browser** for **firefox** in the script. x-www-browser is only a link to your main browser.

---

### Post by cosine352 on 2009-08-26
> **matthewbpt said:**
> I install a package called 'checkgmail'. It also resides in your system tray and checks your gmail account automatically, and when you hover your mouse over it you can see what the emails are and even read them if you like, and if you click on the icon it will open your gmail in firefox (or another browser of your choice). In the configuration it also has a field for 'Launch command when mail is received' and I put the following in there 'paplay /path/to/sound/file', choosing an appropriate sound file, and now whenever I receive mail I get a sound notification, very handy.

:guitar::guitar::guitar::guitar::guitar:

---

### Post by Buschbarber on 2009-08-26
> **cosine352 said:**
> :guitar::guitar::guitar::guitar::guitar:

Thanks very much!! I tried that and it works fine. The only thing it did not do is display the number of new messages on the face of the icon. Other than that, it worked perfectly, with sound, as well

---

### Post by Buschbarber on 2009-08-26
> **RabbitWho said:**
> there's an ad on for firefox that checks your gmail every five minutes and you can tell it to make a sound in the settings if you like. 

there are two I think, but the one i use is the one that says it's the original.

Do you know which Firefox Addon it is? The only thing about a Firefox Addon, for Gmail, is that you have to have Firefox open to use it. These other options, such as Mail Notification, monitor my Gmail Inbox and let me know when I have new mail. At that point, one click opens Firefox and logs me in to Gmail.

---

### Post by Buschbarber on 2009-08-26
> **danielrmt said:**
> I suppose you are using KDE? The best way would be setup Firefox to be your main browser. I can't help you with that in KDE. Other way is to replace **x-www-browser** for **firefox** in the script. x-www-browser is only a link to your main browser.

Actually, I only tried KDE and XFCE once, each, and then returned to using Gnome. I just checked Preferred Applications and Firefox is still my default Web Browser. I substituted the word firefox for x-www-browser and it now launches Firefox.

When I click on a Web Link, in an email message, Firefox launches as the default.

Any idea why I was getting Konquerer when using your original script?

Also, how do I close Mail Notification if I want to run something else?

---

### Post by Tibuda on 2009-08-26
> **Buschbarber said:**
> Any idea why I was getting Konquerer when using your original script?
No idea. Try typing this in a terminal to see where x-www-browser goes:
```
ls /usr/bin/x-www-browser -l
ls /etc/alternatives/x-www-browser -l
```

> Also, how do I close Mail Notification if I want to run something else?
I don't understand what you mean. Mail notification runs in the background, so you can always run "something else". To "close it" you can kill it using the gnome system manager.

---

### Post by Buschbarber on 2009-08-26
> **danielrmt said:**
> No idea. Try typing this in a terminal to see where x-www-browser goes:
```
ls /usr/bin/x-www-browser -l
ls /etc/alternatives/x-www-browser -l
```

Here are the results of the code you asked me to run:

rich@UE23:~$ ls /usr/bin/x-www-browser -l
lrwxrwxrwx 1 root root 31 2009-07-24 20:39 /usr/bin/x-www-browser -> /etc/alternatives/x-www-browser
rich@UE23:~$ ls /etc/alternatives/x-www-browser -l
lrwxrwxrwx 1 root root 18 2009-08-11 01:21 /etc/alternatives/x-www-browser -> /usr/bin/konqueror
rich@UE23:~$ 



I don't understand what you mean. Mail notification runs in the background, so you can always run "something else". To "close it" you can kill it using the gnome system manager.


I realize that I can run more than one app at a time.

As I test each of these Notifiers, I only want one running at a time, otherwise, the Sound Notification is not going off, multiple times, each time they check for new messages.

Mail Notification doesn't happen to have a Quit option on the menu. When I went into System Monitor to End the Mail Notification process, it warned me:

Ending a process may destroy data, break the session or introduce a security risk. Only unresponding processes should be ended.

What is the difference between Ending a process and Killing a process?

---

### Post by Buschbarber on 2009-08-26
For some reason, Mail Notification does not display a number larger than 20, on it's icon, for the number of new messages.

Also, the number reflects the number of UnRead Messages, not the number of New Messages, since the last time I checked my Gmail InBox.

Since I sometimes receive 90 messages per day, if I am away from the house all day, the number displayed is not very useful if it maxes out at 20.

---

### Post by Tibuda on 2009-08-26
> **Buschbarber said:**
> I realize that I can run more than one app at a time.

As I test each of these Notifiers, I only want one running at a time, otherwise, the Sound Notification is not going off, multiple times, each time they check for new messages.

Mail Notification doesn't happen to have a Quit option on the menu. When I went into System Monitor to End the Mail Notification process, it warned me:

Ending a process may destroy data, break the session or introduce a security risk. Only unresponding processes should be ended.

What is the difference between Ending a process and Killing a process?

Sorry, now I understand what you want. No harm if you end/kill mail-notification. That message is to avoid to stop an important system proccess like  hal, gdm or Xorg. If you don't know what a process is, dont kill it.

---

### Post by Buschbarber on 2009-08-26
Thanks!! I did not know how to close the program gracefully

---

