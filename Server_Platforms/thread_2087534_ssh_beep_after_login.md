---
title: "ssh beep after login"
date: 2012-11-23
forum: Server Platforms
---

### Post by Gareth_2007 on 2012-11-23
Evening all,

After some recent issues with gain ssh access i would like to add a beep when there is a successful ssh login.

I have install  the beep package and unblack listed the internal speaker and it works file.

any suggestions on where the add the beep -r 5 command?

(i have also researched and followed steps on making ssh more secure :) )

Thanks

---

### Post by papibe on 2012-11-23
Hi Gareth_2007.

I would go with ~/.profile as it is executing when you login. Add a line at the end of the file.

Let us know how it goes.
Regards.

---

### Post by Lars Noodén on 2012-11-24
If you are talking about making a sound any time anyone logs in then there is sshrc.  The script /etc/ssh/sshrc gets run every time there is a successful login via SSH.  So you could put something there to make a sound.

If you want just one user and not all of them, then ~/.ssh/rc gets run if it exists.

---

### Post by Lars Noodén on 2012-11-24
You can send audio to the speaker from any user using 'play'

```

/usr/bin/play /usr/share/sounds/ubuntu/stereo/phone-incoming-call.ogg > /dev/null

```

---

### Post by markbl on 2012-11-24
> **papibe said:**
> 
I would go with ~/.profile as it is executing when you login. Add a line at the end of the file.
If you go this way then make sure you wrap it with a test to run it only on a ssh login, e.g:
```

if [ -n "$SSH_TTY" ]; then
    beep -r 5
fi

```

---

### Post by Lars Noodén on 2012-11-24
If it's a busy server you could even give unique ringtones to the users.  [ssh and sshd set some environment variables](http://en.wikibooks.org/wiki/OpenSSH/Server#Environment_Variables) including ${USER}, which can be used in a case statement or something similar.

---

### Post by papibe on 2012-11-24
following Lars train of thought...

You can even install alsa, espeak, you could 'say' the name of the user (along with a custom greeting message if you want).

Regards.

---

### Post by Gareth_2007 on 2012-11-29
> **Lars Noodén said:**
> If you are talking about making a sound any time anyone logs in then there is sshrc.  The script /etc/ssh/sshrc gets run every time there is a successful login via SSH.  So you could put something there to make a sound.

If you want just one user and not all of them, then ~/.ssh/rc gets run if it exists.

I went with this and it worked fine. i used beep -l 300 -f 329.6 -n -l 300 -f 370 -n -l 300 -f 523.2 to make the sound i wanted.

Many thanks to every one for there input.

---

