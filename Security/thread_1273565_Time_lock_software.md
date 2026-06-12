---
title: "Time lock software"
date: 2009-09-23
forum: Security
---

### Post by Bramkaandorp on 2009-09-23
Does anyone know of a program which can lock (encrypt) a file and/or folder for a certain amount of time, after which it will unlock (decrypt) itself?

And if there is no such program, is there some way of getting this done in another way?

Thanks in advance.

Bram

---

### Post by doas777 on 2009-09-23
well you could use truecrypt for the cryptography, but you could script it's controls via python or shell or whatever.

---

### Post by openfly on 2009-09-23
You could probably go into the LUKS source and modulus jiffies for the value of a day on your arch / config then just figure out the differentials for the times you want to disallow decrypt functions from running and just handle it in simple logic.

It wouldn't be TOO hard of a modification.

---

### Post by Bramkaandorp on 2009-09-23
You do make it sound easy, I have to give you that.

Sadly, I have little idea of what you just said, since I am just a computer user, not really a coder or modifier of files.

If you would like to explain further what you mean, I'll see how easy it really is, and maybe I will try it. Right now, I'm like a carpenter in a nuclear facility: out of my element (no pun intended).

Cheers,

Bram

---

### Post by openfly on 2009-09-23
Maybe I'm wrong, but my guess is plenty of carpenters have plied their trade in nuclear facilities.

---

### Post by doas777 on 2009-09-23
well, the commands to mount and dismount a truecrypt archive are:

```

truecrypt <path to archive> <path to mountpoint>
truecrypt -d <path to archive or mountpoint>

```
(you will likely have to use a force parameter on the dismount command so that it will close even if files and windows are open to it).

so all you really need is a way to tie those two commands together with a timer. a simple python script or even a cron job may accomplish what you want.

---

### Post by Bramkaandorp on 2009-09-23
@Openfly: The comparison was not the best, I know. But you get the point, right? I know how to change some parameters in a Gtk theme, but this sort of thing is a bit above my level.

Don't get me wrong, I am keen to learn. Learning is good.

@doas777: It sounds logical to me.

If anyone knows a way, I would be very grateful.

I couldn't find anything on the web, and since I may not be the only one in need of this, I spoke out.

Cheers

---

### Post by Sarmacid on 2009-09-23
Depending on how well encrypted you need this information, you could go with either symmetric or asymmetric encryption(Both provided by gpg, for which you don't have to install anything) and then just make cron run your command or script.

---

### Post by doas777 on 2009-09-23
> **Sarmacid said:**
> Depending on how well encrypted you need this information, you could go with either symmetric or asymmetric encryption(Both provided by gpg, for which you don't have to install anything) and then just make cron run your command or script.

FYI op, symmetric is for your data. asymmetric is for data you share with others. i recommend symmetric for inhouse stuff.

---

### Post by scorp123 on 2009-09-23
> **Bramkaandorp said:**
> Does anyone know of a program which can lock (encrypt) a file and/or folder for a certain amount of time, after which it will unlock (decrypt) itself? Hmmm ... the inverse is certainly possible, e.g. with programs such as **cryptkeeper** ... If it reaches a certain time-out it will unmount the configured crypto-folders again. Very useful if you want to make sure that nobody can walk up to your laptop and browse through your files while you are away ...

But you want the exact opposite of this... May we ask why? Maybe there is an easier way to achieve whatever you want to achieve?

---

### Post by Bramkaandorp on 2009-09-23
I want to achieve the following:

A file (.avi to be specific) which is locked for a certain time, and which unlocks itself when its time is up.

Something like a "do not open before Christmas" note, but a bit more enforced.

The use: general, but mostly personal. I want to be able to send someone a birthday card which only opens on someone's birthday, no earlier. But that's just an example which popped in my head.

The idea (which is not original: search for TimeLock, a program for Windows) just came to me.

Cheers,

Bram

---

### Post by scorp123 on 2009-09-24
> **Bramkaandorp said:**
>  A file (.avi to be specific) which is locked for a certain time, and which unlocks itself when its time is up. 
OK ...

> **Bramkaandorp said:**
>  Something like a "do not open before Christmas" note  Linux being a multi-user system could do this even without encryption and what not. Encryption in fact seems very redundant to me.

Why not record your message, then place the file into another user account (or even another computer?) and then have "at" (see the manual: **man at**) deliver the message at a specified time?

If the target user (e.g. your kid?) doesn't have admin access to the "root" account (e.g. can't operate "sudo") then you could use the "root" account directly to hide your message. "at" would then simply deliver it at a specified moment in time. I guess one good place to deliver a recorded message to would be the desktop of the target user? The command line could look like this (this is assuming that you are executing this under the "root" account):

```
# move the recorded message away to root's account
sudo mv /home/myUser/tmp/MyRecordedMessage.avi /root/

# trigger "at" so it will deliver the message on
# September 25, 2009, at 17:30
# - enter commands one by one, terminate each line with the ENTER key
# - when done press CTRL+D
# - when CTRL+D is pressed "at" will respond with "EOT"
#

> sudo at 17:30 sep 25
warning: commands will be executed using /bin/sh
at> cp /root/MyRecordedMessage.avi /home/targetUser/Desktop/
( ... ENTER ... )
( ... then pressing CTRL+D ... )

at> <EOT>
job 1 at Fri Sep 25 17:30:00 2009

``` If "at" shows a response like this then it means it has accepted the job. You can check the "at" queue with this command:
```
sudo atq
```

"atq" will respond like this:
```
> atq
1	Fri Sep 25 17:30:00 2009 a root

```

That first number is the job ID ... So if you want to check what the job will do, you'd type:
```
sudo at -c 1
```

This will spit out a lengthy listing of environment variables and the actual script "at" will try to execute.

I mentioned above that you could hide the recording on another computer. For this to work you'd need to setup SSH keys:
[http://www.debian-administration.org/articles/152](http://www.debian-administration.org/articles/152)

And the command that would need to be executed by "at" is this one:
```
scp remoteuser@server:/path/to/file /home/targetUser/Desktop/
```

You could execute this as "root" on your side so this "at" job remains hidden from the target user. And executing it this way (e.g. have the target PC download the file instead of pushing it onto the target PC) has the advantage that you don't have to open up your "root" account for remote SSH access (if you do it right then your "root" can do a password-less login onto the normal user account on the remote machine but not the other way round; i.e. you don't exchange root's SSH keys with the other machine).

---

### Post by Bramkaandorp on 2009-09-24
No, not a kid (not married and never in a relationship). No one in particular.

It's not quite what I mean, even though the idea is interesting.

Let's sketch a situation:

Someone creates a game which is very highly anticipated. Now, usually people compress the files in winrar, and lock it with a password, which is released on the day that the password free version is officially released.

In stead of this, a time lock might be more suitable.

Again, this is just an example, but it sketches the point better. I hope it is useful.

---

### Post by openfly on 2009-09-24
> **Bramkaandorp said:**
> No, not a kid (not married and never in a relationship). No one in particular.

It's not quite what I mean, even though the idea is interesting.

Let's sketch a situation:

Someone creates a game which is very highly anticipated. Now, usually people compress the files in winrar, and lock it with a password, which is released on the day that the password free version is officially released.

In stead of this, a time lock might be more suitable.

Again, this is just an example, but it sketches the point better. I hope it is useful.

In that situation you'd send the game data over compressed and encrypted... then provide the decrypt key on game release date.

Simple.

---

### Post by Bramkaandorp on 2009-09-24
It was just an example where a timelock would make more sense.

If I would have the file, and I want to install the game years later, maybe the site is down (in the case of Forgotten Hope WWII mod for Battlefield 2, they post the unlock code on their home page), or I have removed the mail to save room. Then the file would be useless.

A timelock would mean that I can not use the game befor the official release date, but after that, I am free to use it whenever I want, without having to keep a document or mail with the code.

As I said, there is a program for Windows which does this, so it is possible. The program in question does it poorly (imho), but the possibility is there. "We have the technology".

So if the possibility is not yet there in an "regular user" way, then I will have to wait 'till there is. I am not, an never will be a good coder, so making it myself is out of the question.

Cheers,

Bram

---

### Post by scorp123 on 2009-09-24
> **Bramkaandorp said:**
>  So if the possibility is not yet there in an "regular user" way Nobody is stopping you from using "**mcrypt**" and combine it with my "at" examples above ...
```
sudo apt-get install mcrypt
```

I'd recommend you read the "man" page:
```
man mcrypt
```

In short .... To encrypt a file:
```
mcrypt file
```

To decrypt a file:
```
mcrypt -d file
```

And yes, you could combine it with my "at" examples above so the encryption or decryption happens at a specified time. As "at" won't support prompting for the password in an interactive way you will have to use the "**-f**" parameter and supply the encryption/decryption password in there.

e.g. to use your own SSH public key (why not? it certainly works ... :) ) as a "password" you'd type:

To encrypt:
```
mcrypt -f ~/.ssh/id_rsa.pub /path/to/file
```

To decrypt:
```
mcrypt -d -f ~/.ssh/id_rsa.pub /path/to/encrypted.file
```

I'd recommend you test this with "at" above before you use it for real.

---

