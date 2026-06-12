---
title: "Upgraded by updating sources.list"
date: 2013-11-02
forum: Ubuntu Development Version
---

### Post by A.O._Stanley on 2013-11-02
Per grahmmechnical, ran the following:

```
sudo sed -i 's/trusty/saucy/g' /etc/apt/sources.list 
```

Then ran:

```
 sudo gedit /etc/apt/sources.list
```

Then I scrolled down to the bottom of the list and put # in front of the last two entries. Saved and exited.

Then I ran:

```
sudo update-manager -d
```

And was given the option to upgrade to Trusty.

So that method is working now.

---

### Post by grahammechanical on 2013-11-02
I need to make a correction. Actually Ventrical pointed this out. The code should be

```
sudo sed -i 's/saucy/trusty/g' /etc/apt/sources.list
```

In effect the command says to change the old code name to the new code name. So, it would be precise to quantal; quantal to raring; raring to saucy and saucy to trusty.

So, A.O_Stanley, Welcome to Ubuntu+1 testing. Have fun.

I see that we are getting trusty ISO images at 

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds)

So, we could use one of those images to fresh install trusty and test the image at the same time. Or upgrade from the image which would also be a form of testing.

Regards.

---

### Post by zika on 2013-11-02
> **A.O._Stanley said:**
> Per grahmmechnical, ran the following:

```
sudo sed -i 's/trusty/saucy/g' /etc/apt/sources.list 
```

Then ran:

```
 sudo gedit /etc/apt/sources.list
```

Then I scrolled down to the bottom of the list and put # in front of the last two entries. Saved and exited.

Then I ran:

```
sudo update-manager -d
```

And was given the option to upgrade to Trusty.

So that method is working now.Whole gymnastics of changing sources.list was completely unnecessary at this moment. Last command would have worked the same without that change...
Editing of sources.list is neccessary only in very early stages of testing, better to say when testing even did not start at all... At those stages even &#8222;Debian way&#8220; of upgrade is recommended...
Caveat: Before (any) upgrade turn off all additional PPA's and (for some, even) contemplate of doing ppa-purge of those...

---

