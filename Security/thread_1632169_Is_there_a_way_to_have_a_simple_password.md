---
title: "Is there a way to have a simple password?"
date: 2010-11-27
forum: Security
---

### Post by CF_Smith on 2010-11-27
Hey,

I am new to the whole Linux operating system, I installed Maverick Meerkat as a dualboot on my windows machine. During the installation I was forced to generate a 'good' password. after a few frustrated attempts I finally generated a 'good' password which consisted of nine letters, a punctuation and five numbers.  This is ridiculous to type in every time I wish to install an application.  I tried to make my password more simple by going through the 'Users and Groups' setting but I can still only change my password to a 'good' one.  Is there anyway to make my password a simple six letter word?

---

### Post by Enigmapond on 2010-11-27
Your password can be whatever you want. It just suggests that it's good or bad. In truth, it can be just a letter or number. You can change it to whetever you want in System/Administration/User and Groups.

---

### Post by CharlesA on 2010-11-27
I've installed Lucid and Maverick a few times and it's always allowed me to use whatever password I wanted (weak or not).

You should get a confirmation box asking if you are sure you want to use a weak password or not.

---

### Post by CF_Smith on 2010-11-27
> **Enigmapond said:**
> Your password can be whatever you want. It just suggests that it's good or bad. In truth, it can be just a letter or number. You can change it to whetever you want in System/Administration/User and Groups.

Whenever I try to change my password I get this[IMG]http://i591.photobucket.com/albums/ss355/Yamaha_James/password.png[/IMG]  as a result.

---

### Post by CF_Smith on 2010-11-27
> **CharlesA said:**
> I've installed Lucid and Maverick a few times and it's always allowed me to use whatever password I wanted (weak or not).

You should get a confirmation box asking if you are sure you want to use a weak password or not.

I have installed Karmic Koala on this machine but the drivers did not work, however I was able to have anything as a password, upon installation of Maverick Meerkat, it would only let me choose a stong pass word.

---

### Post by Enigmapond on 2010-11-27
> **CF_Smith said:**
> Whenever I try to change my password I get this[IMG]http://i591.photobucket.com/albums/ss355/Yamaha_James/password.png[/IMG]  as a result.

Wow! First time I ever saw a Nazi-like warning regarding a password. Must be a 10.10 thing...how very odd and a bit much.

---

### Post by CF_Smith on 2010-11-27
I know right? It sucks because my machine doesn't like to run previous versions... There must be a way around this though?

---

### Post by akand074 on 2010-11-27
My password just consists of 7 digits in Maverick. I'm sure you could do a simple 6 figure password, try all numbers or else a more simple alphanumeric password.

---

### Post by The Cog on 2010-11-27
Try using the command **passwd** from a command prompt. It will ask for your current password and then the new password. I can't remember how fussy it is about password strength.

---

### Post by CharlesA on 2010-11-27
> **The Cog said:**
> Try using the command **passwd** from a command prompt. It will ask for your current password and then the new password. I can't remember how fussy it is about password strength.

It's not fussy about password strength. The only hitch with that is that it doesn't change yer keyring password.

---

### Post by CF_Smith on 2010-11-27
> **The Cog said:**
> Try using the command **passwd** from a command prompt. It will ask for your current password and then the new password. I can't remember how fussy it is about password strength.

Even that did not work. However I got my father to help me out a little. He had to type in sudu to force a password onto root, then log into root, then set the password for my user as root. All doen via terminal of course. Thanks for the help guys!:D

---

### Post by Enigmapond on 2010-11-27
That might be a quick fix but running your machine as root is _definitely_ not a good thing...

---

### Post by CharlesA on 2010-11-27
> **CF_Smith said:**
> Even that did not work. However I got my father to help me out a little. He had to type in sudu to force a password onto root, then log into root, then set the password for my user as root. All doen via terminal of course. Thanks for the help guys!:D

Er. You should have been able to just use ***sudo passwd yourusername*** and it would have worked fine. No need to activate the root account.

---

### Post by CF_Smith on 2010-11-27
> **Enigmapond said:**
> That might be a quick fix but running your machine as root is _definitely_ not a good thing...

I am using my user now, the root was to force the password.

---

### Post by CF_Smith on 2010-11-27
> **CharlesA said:**
> Er. You should have been able to just use ***sudo passwd yourusername*** and it would have worked fine. No need to activate the root account.

We tried that and got this [IMG]http://i591.photobucket.com/albums/ss355/Yamaha_James/password2.png[/IMG]

---

### Post by sisco311 on 2010-11-27
> **CF_Smith said:**
> I am using my user now, the root was to force the password.

As CharlesA already pointed it out, you don't have to set up a root password to run a command ( or a shell ) as root:
```
sudo passwd **username**
```
where **username** is your login name.

See: [uhelp]community/RootSudo[/uhelp]

If you wish to lock the root password again:
```
sudo usermod -p '!' root
```

---

### Post by HermanAB on 2010-11-28
Howdy,

Yes, with some effort, you can set a k4wl 4 character password and in a few weeks, you can be one of the "OMFG my Ubuntu was h4ck3d!!!" posters on these forums...

There are numerous reasons why Unix security works the way it works.  You got to get used to it and not try to change it into a trojan infested Windows copy.

---

### Post by theDaveTheRave on 2010-11-29
I suggest it depends on what you consider simple?

I have a 'strong' 6 alhpa-numeric password I created. Now I use this password, and then append it with the password for various other things (or use a date) for various connections.

eg. Lets say you have a favorite movie or book quote.
Lets take an appropriate saying from isaac assimov, about the 3 rules of robotics...

> 
1.A robot may not injure a human being or, through inaction, allow a human being to come to harm.
2. A robot must obey any orders given to it by human beings, except where such orders would conflict with the First Law.
3. A robot must protect its own existence as long as such protection does not conflict with the First or Second Law


Now take a date you'll remember for some reason (you could use your birthday, but that reduces the power of the whole thing a little bit as everyone is going to know your birthday.

Lets use use [January 1st 1970]("http://en.wikipedia.org/wiki/Unix_time").

Now we take the standard year date as 19700101 (or any other standard you may fancy)

I now start working through the characters in my quote.

```

1 = A
19 = a
197 = (err...whatever),

```

As you can see this is going to create what in all attempts appears as a very random set of characters.

I you forget your password, no problem, you know the 'favourite quote' and you know your 'special date' so you can easily (or faily easily) re-determine your password.

For me I would now take this password, and append it to the front of a web site name...

EG. AahcLmsUbuntuForums - could theoretically be my login password for the ubuntu forums.

I have done the same for cumputer, servers, varous equipment. Maybe I change the details of the 'favourite quote' sometimes for specific reasons - eg I use a home 'quote' a works 'quote' and a for everything else 'quote'.

One word of warning, I don't recomend using a really famous quote, the title of a film isn't going to be so good (how many times have you said 'My favourite film is...... ').

Anyway, thats how I do it. And after a few goes it becomes easy to remember - change a few characters for numbers and its an even harder password to crack. My passwords come up 'very strong' every time, and the base is only 6 alpha-numerics long.

So that is my way of creating 'strong' passwords, and at least I can re-create them if I do forget them!

David

---

