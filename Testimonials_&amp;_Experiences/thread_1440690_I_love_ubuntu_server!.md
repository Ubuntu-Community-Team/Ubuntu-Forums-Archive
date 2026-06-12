---
title: "I love ubuntu server!"
date: 2010-03-27
forum: Testimonials &amp; Experiences
---

### Post by tica vun on 2010-03-27
Wow, I put ubuntu server on an old PC that's been collecting dust in my basement today. I never imagined setting up a website is so simple. With the documentation at ubuntu.com/server and a php manual, I was able to install LAMP, put together this site that prints fortune | cowsay and host it on my own, in ten minutes.

[http://sshbox.ath.cx](http://sshbox.ath.cx)

:D

---

### Post by NightwishFan on 2010-03-27
I can ping the url, but nothing shows up except an error.

---

### Post by phrostbyte on 2010-03-27
```

 ________________________________________
/ When it comes to broken marriages most \
| husbands will split the blame -- half  |
| his wife's fault, and half her         |
\ mother's.                              /
 ----------------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

```

:D

---

### Post by NightwishFan on 2010-03-27
It works now, excellent. I am glad it worked out so well for you.

---

### Post by _h_ on 2010-03-27
```
 _________________________________________
/ It hangs down from the chandelier       \
| Nobody knows quite what it does Its     |
| color is odd and its shape is weird It  |
| emits a high-sounding buzz              |
|                                         |
| It grows a couple of feet each day and  |
| wriggles with sort of a twitch Nobody   |
| bugs it 'cause it comes from a visiting |
| uncle who's rich!                       |
|                                         |
\ -- To "It Came Upon A Midnight Clear"   /
 -----------------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

```


lol....what?

---

### Post by skierkyles on 2010-03-27
If you dont mind me asking, how are you getting php to run fortune/cowsay?

right now I have...
```
print system('cowsay "Kyles World"');

```
And nothing is appearing, but I know my php install is working, because a-lot of other commands work... Just not cowsay and forutne.

/php noob/

---

### Post by tica vun on 2010-03-27
You have to enter the full path to anything that isn't in /usr/bin .

```

<?php
   $output = shell_exec('/usr/games/fortune | /usr/games/cowsay');
   echo "<pre>$output</pre>";
?>

```

---

### Post by jpeddicord on 2010-03-27
*Thread moved to **Ubuntu Testimonials & Experiences**.*

---

### Post by Austin25 on 2010-03-30
I love it! This makes me want to start a server.

---

