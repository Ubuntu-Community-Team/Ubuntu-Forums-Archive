---
title: "giving low level user permission to run a program"
date: 2006-02-28
forum: Server Platforms
---

### Post by jezjones on 2006-02-28
Hi there everyone,

I hope that this is going to be pretty easy... its just not something i have done before and i cant seem to find any documentation that specifically covers it.

I would like to let the nobody user run a program called mpg321.
This is for a dev server on a local lan, so that we can play music via a web interface.

Thanks

Jez

---

### Post by localzuk on 2006-02-28
The easiest thing to do is to add the nobody user to a new group - name this whatever you wish. Also, set the owner group of the program to equal this group.

Then set group to have execution permissions.

To do this from commandline you would type:
```

sudo groupadd mpg321grp
sudo usermod -G mpg321grp username
sudo chgrp mpg321grp /usr/bin/mpg321
sudo chmod g+x /usr/bin/mpg321

```

I believe that should work.

---

### Post by localzuk on 2006-02-28
Hmm... After trying it myself - it doesn't seem to have worked. If you could post here if it works for you, that'd be great :)

---

### Post by localzuk on 2006-02-28
On second thoughts. That seems to remove all your other groups? Hmm... I will investigate further. Don't run those commands though.

---

### Post by Corvillus on 2006-02-28
I thought you could run mpg321 regardless of user privileges (since it defaults to a+x). That said, the nobody user probably doesn't specifically have audio device access privileges, in order to have those you need to be in the audio group. To add the user to that group, use the following:
```
sudo gpasswd -a nobody audio
```

---

### Post by localzuk on 2006-02-28
Ah, I hadn't thought of that. Oh well. :)

---

### Post by jezjones on 2006-03-01
Hi and thanks for the replies.

What i did first was to add the nobody user to the 'users' group, which is the group that my normal login is in. I figured if i can use the app when i log in myself then it should work for other people in the group.

So when i did that, it does work, but you rightly say that at that point it fails due to permissions on the audio device. The specific error refers to a 'suitable' libtao driver'.

Any idea how i can tell which device is my audio device, i seem to have alot of stuff in /dev

Thanks again for your answers.

---

### Post by localzuk on 2006-03-01
you need to add the user to the 'audio' group also.

Why are you wanting to give 'nobody' permissions?

It would be more advisable to run your web apps as a custom user and give that permissions instead.

---

### Post by jezjones on 2006-03-01
I have done that, but it still does not work.

I went the nobody route as that is the apache user, there was no better reason than that. 
I did try and change the user that apache runs as to a normal user account to see if it had a different effect but still the same.

In terms of user security and keeping the web server secure, that is not a concern as it is on a closed lan and more to see if i can do it than anything else.

I think i know where the problem is happening. If i su to either a normal user account, root or nobody, I can run the mp3 player from the command line.
It is only when i do it from a php page that it throws the error to the apache error log. I am using exec from the the php page and safe mode is off in the apache conf.

Is there some difference between the shell (like bash) and where the shell commands from apache get run ?

---

### Post by jezjones on 2006-03-01
SUCCESS!!!!

After my last post which showed that the user 'nobody' could run the program, but not from the web left me thinking that this was not a permissions issue anymore.

So looking into the php / apache side of things I found that the reason for it not working was the 

"options IncludesNoExec" 

directive in the apache conf file. Removing this to allow for exec made it work.

Just to prove the security access of the low level user, i modified my page to add a link that does a 'exec "killall mpg321" to stop the music playing.

Thanks to everyone who helped me on here. 
It's been a while since i did something with linux "just to see if i can" rather than the day to day stuff i have to do as part of work or home life.

---

### Post by LordHunter317 on 2006-03-01
[QUOTE=jezjones]I have done that, but it still does not work.

I went the nobody route as that is the apache user, there was no better reason than that. [/quote]Nobody shouldn't be the Apache user.  In fact, it's a very bad thing to have Apache use the nobody account.

And if you want remote contorl of music, this is a bad way to go about it.  Use SSH and your regular user account, or a special account using keypairs and limited access to do it.

---

### Post by jezjones on 2006-03-01
Well actually the user account nobody is the default apache account in 1.3, which is the version i am using, and I did mention that security was not a consideration.

As for using ssh for the music, what is the point of that? 
I can do it at the command line already!
The reason for using a web browser is to get nice dynamic lists of the music from the folders on the server and having pointy clicky things.
Non-linux people are not very impressed when you show then an ssh window, they just go glassy eyed, but a nice pointy clicky thing and they respond with the appropriate oohs and aaahs.

If i was after a decent mp3 player application to play music i would just use one (xmms?), but this was an excercise in doing something different. 

For instance i have an old x-box at home, running linux. I could make that into a dedicated music player on my home lan and then the music in the house could be controlled by anyone on the lan with a web browser.

I appreciate you taking time to advise on this, and if i ever considered putting this onto any kind of production system then it would be thought through alot more... this time round though it is just a fun excercise to see how apache and user accounts work.
For one thing I am now alot more familiar with the IncludesNoExec directive so i can ensure that things are more secure in future.

---

### Post by LordHunter317 on 2006-03-01
[QUOTE=jezjones]Well actually the user account nobody is the default apache account in 1.3, which is the version i am using, and I did mention that security was not a consideration.[/quote]Not in the packages, it isn't.

And even if it's the apache source defaults, it's incorrect.  The documentation says as much, IIRC.

> As for using ssh for the music, what is the point of that? 
I can do it at the command line already!Because it's more secure.

> The reason for using a web browser is to get nice dynamic lists of the music from the folders on the server and having pointy clicky things.And there are still better ways to achieve control over the actual player.

---

### Post by jezjones on 2006-03-01
Ok smart arse, how do you get the oracle instant client running with the packages? As this needs a re-compile of both php and apache.
This is a dev server sitting on my desk, it needs to be connected to by me and 2 colleagues within a very secure network.

Also i downloaded the source of 1.3 from the apache foundation website. The httpd.conf has the default user set to nobody, that seems like a default to me.

Doing it with SSH may be secure but it is the same as not doing it or using a local mp3 player, not everything in life is about security.

I am trying not to find your responses a dismissive and cynical, you've said there are better ways of controlling the player but you haven't suggested any.

I did specifically say that security was not an issue as i am aware this is the server forum where most people are dealing with production systems and security is a major concern.

In all honesty if someone wanted something like this then there are loads of solutions out there, maybe even running a shoutcast server would be an alternative, but this is just a little excercise to try something i haven't tried before.

---

### Post by localzuk on 2006-03-01
As you are interested in remote audio control - you may like to look at this page: [http://rousse.pm.org/~georgi/xmms/](http://rousse.pm.org/~georgi/xmms/)

Also, regarding security - the point I think people are trying to make is that even on a 'very secure network' it is important to start with security then functionality - as it gets you to work in that frame of mind. The things that come to mind is that you state 2 other people have access to the server. What if they also do some odd things and they intefere due to you having given nobody too many privileges?  (Bear in mind that sometimes things aren't done on purpose, they can be accidental eg. a script that should delete all the files in a specific directory accidentally is programmed to delete all files in the root directory but wouldn't have been able to do it normally with nobody but can now due to these privileges). What if the computer can be connected to via the internet somehow?

We are only trying to help - don't take our comments as personal attacks as they more than likely aren't.

---

### Post by LordHunter317 on 2006-03-01
[QUOTE=jezjones]Also i downloaded the source of 1.3 from the apache foundation website. The httpd.conf has the default user set to nobody, that seems like a default to me.[/quote]And I said, that default is wrong and the documentation says as much.

> I am trying not to find your responses a dismissive and cynical, you've said there are better ways of controlling the player but you haven't suggested any.Yes, I did.

> I did specifically say that security was not an issue as i am aware this is the server forum where most people are dealing with production systems and security is a major concern.Then disregard it, and consider my notes as warning for other people who can't afford to disregard security.

---

### Post by jezjones on 2006-03-01
Ok, I take that on board and apologise for my outburst.
It would be nice to think that if i am doing it the wrong way then people would suggest an alternative (as you have localzuk) rather than just saying it is insecure and wrong.
I am the first to admit that alot of people know alot more about linux than me, and i want to learn.

Ironically one of the main things that i have learned from this is how much security there is in place, i.e. just what i turned off to achieve this.

Thankyou to everyone who took the time to respond to this.

---

