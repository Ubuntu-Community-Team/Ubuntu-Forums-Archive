---
title: "Help with gnu screen -dmS &amp; screen -X"
date: 2014-02-04
forum: Server Platforms
---

### Post by arsenic23 on 2014-02-04
I'm using screen to run a simple server application:
```
screen -dmS pie mything.sh
```

I then went a wrote a python script that passes it commands on a cron job using:
```
screen -S pie -X stuff $'my commands\n'
```

This worked great while I was playing with it but then I quickly realized that after restarting the screen session / server screen -X does not work until I attach and unattached the screen session once.  So now a huge amount of work is down the drain since my stuff requires human interaction when the server application comes down for maintenance every Sunday.  For those of you more familiar with screen, is there something I can do to make screen -X work without attaching the screen session with -x/-r and then detaching it with ctrl+a,ctrl+d?

I've been looking for information on this for two days now and have had no luck.

---

### Post by CharlesA on 2014-02-04
I used to use:

```
screen -d -m script.sh
```

The screen session will start detached, but will close once the script is finished.

---

### Post by arsenic23 on 2014-02-04
> **CharlesA said:**
> I used to use:

```
screen -d -m script.sh
```

The screen session will start detached, but will close once the script is finished.

I think you misunderstood.  The script never finishes; it launches a server with a prompt.  I'm injecting commands into the prompt with 'screen -S pie -X stuff', but it only works after it's been entered with screen -r pie and then detached again.  I have no idea what causes this behavior or how to get around it.

----------------------------------
EDIT:   Here's how you can try it yourself.

```

screen -d -m -S pie
screen -S pie -X stuff $'\necho pie\n'
screen -S pie -X stuff $'\necho pie\n'
screen -S pie -X stuff $'\necho pie\n'
screen -S pie -X stuff $'\necho pie\n'
screen -r pie

```

You can see that the commands did not get inserted into the screen session.
Then detach the screen with ctrl+a followed by ctrl+d.   Now:
```

screen -S pie -X stuff $'\necho yes\n'
screen -S pie -X stuff $'\necho yes\n'
screen -S pie -X stuff $'\necho yes\n'
screen -r pie

```

Now the commands did get inserted into the screen session.  I need a way to get to this point without human input.  I don't understand why it doesn't work to begin with.

---

### Post by CharlesA on 2014-02-04
[This]("http://stackoverflow.com/questions/4440633/how-can-i-send-stuff-commands-to-a-start-in-detached-screen") is also demonstrating what you are seeing. Maybe it'll help?

---

### Post by arsenic23 on 2014-02-04
Thank you.  That looks like it'll work.
I have no idea why that didn't show up when I was searching around for answers.

OK, I tried it out and it works perfectly.  I've only been using screen for a short time and didn't realize -X did anything other then stuff, although I suppose it should have been apparent.
Thank you again.

---

