---
title: "[SOLVED] Making text during boot sequence... colored"
date: 2007-08-11
forum: Server Platforms
---

### Post by southernman on 2007-08-11
Is it possible to have colored text displayed in the console during the boot sequence?
If so, please point me in the right direction... I've googled and searched the forums both with no luck.

I've seen this on the SystemRescue CD.

Thanks!

---

### Post by southernman on 2007-08-11
FWIW - I am using Dapper LAMP Server install... no gui! (look ma - no hands!)

I am waiting on my digi cam batteries to juice up so I can take a picture of the monitor screen and highlight what I'd like to have colored in case what I asked isn't exactly clear as mud.

In hindsight, this probably belongs in the General Discussions forum... Would a moderator please move it there. Thank you.

---

### Post by bodhi.zazen on 2007-08-12
See if this link helps :

[https://help.ubuntu.com/community/BootText](https://help.ubuntu.com/community/BootText)

---

### Post by southernman on 2007-08-12
Many Thanks bodhi.zazen! I swear that I had Google-d  and searched here. That link did not come up and I went deep into Google results too.

I'll apply that here in a bit, finishing up reconfiguring the kernel, trying to get the TUX logo to show up. With help from this link:

[http://ubuntuforums.org/showthread.php?t=36871]("http://ubuntuforums.org/showthread.php?t=36871")

---

### Post by southernman on 2007-08-12
Just to verify an incosistency here:

The page you linked me to shows this:

> 
echo "$UP$END[ ${GREEN}ok${NORMAL} ]"
else
echo -e "$UP$START $RED*$NORMAL$END[${RED}fail${NORMAL}]"


which is all well and good - however, here is what my file looks like after making the changes as instructed on that link:

> 
echo "$UP$END[ ${GREEN}ok${NORMAL} ]"
else
echo -e " ${RED}failed!${NORMAL}"



Just want to make sure the syntax is correct.

Thank you...

---

### Post by southernman on 2007-08-19
I've finally gotten this figured out. The link bohdi referred me to doesn't work for Dapper. The file you have to edit is actually /etc/lsb-base-logging.sh and this is what I did to get blue brackets and green "ok"

```

$TPUT setaf  4 # blue
printf '[ '
$TPUT setaf  2 # green
printf ok
$TPUT setaf  4 # blue
echo ' ]'
$TPUT op  # normal

```

---

### Post by bodhi.zazen on 2007-08-19
glad it worked for you.

> This aptitude does not have Super Cow Powers. <--- rofl

Ah, but it does !

Try ```
sudo aptitude -v moo
sudo aptitude -vv moo
sudo aptitude -vvv moo
# you get the idea, keep adding -vvvvvv one at a time

Then :

sudo apt-get moo 
```

:twisted:

---

### Post by southernman on 2007-08-19
lol

---

