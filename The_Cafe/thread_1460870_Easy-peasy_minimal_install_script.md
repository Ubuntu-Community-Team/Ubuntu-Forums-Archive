---
title: "Easy-peasy minimal install script"
date: 2010-04-23
forum: The Cafe
---

### Post by Paqman on 2010-04-23
I love the Minimal ISO, but the main question i've got from people when bigging it up is: "How do I know what packages I need to install?"

So i've written a script that will reduce all the messy package witchcraft to a series of yes/no questions.

_Download_

[Perfectminimal]("www.andyduffell.com/perfectminimal")

NB: This script has been tested, but not exhaustively. Consider yourself a tester if you wish to use it at this stage.

_How to use it_

[LIST=1]
[*]Install a command line-only system using the [Minimal ISO]("https://help.ubuntu.com/community/Installation/MinimalCD")
[*]Get the file
```

wget www.andyduffell.com/perfectminimal
```
[*]Make it executable
```

sudo chmod +x perfectminimal

```
[*]And run it:
```
./perfectminimal
```
[/LIST]

_Why bother? What does the minimal ISO do?_

From a single tiny (~12MB!) image you can install any flavour of Linux. My script supports minimal and full installs of Gnome, KDE, XFCE, and LXDE, plus Myth TV (just for fun).

Installing from the minimal means your packages are up-to-date as soon as you install (very handy on older LTS releases). The script supports Hardy, Jaunty, Karmic and Lucid.

_Why is this script asking to install lots of big fat desktop packages?_

Because it's a shameless ripoff of a great script by Robbie Ferguson called [Perfectbuntu]("http://www.category5.tv/linux_scripts/perfectbuntu.php"). Perfectbuntu is designed to automate installation of a smorgasbord of popular desktop software. I've retained all that functionality and extended it to the minimal environment. Even if you're installing ubuntu-desktop and tons of desktop software, there is still some benefit to starting from a minimal install.

_I want more info/I want to help/I've found a bug/I wish to direct a stream of abuse at you_

More info is [here]("http://andyduffell.com/techblog/?page_id=396"). Definitely keen to hear about bugs, or any general comments on your experience. I've got a lot of ideas about ways to improve this script, but i'm sure you've all got better ones, so fire away.

---

### Post by cacycleworks on 2011-09-07
Any chance this can be updated for maverick and/or natty? Or is the intent on sticking to LTS? I did an install on a laptop last night and ended up winging it. I'm doing another friend's laptop tonight, so I'm going to get the 10.04 minimal iso on a usb stick for them so I can try the perfectminimal script.

Thanks!
Chris

---

### Post by Paqman on 2011-09-07
> **cacycleworks said:**
> Any chance this can be updated for maverick and/or natty? Or is the intent on sticking to LTS?

It always supports all currently supported versions of Ubuntu, so it will currently work on Lucid, Maverick and Natty. The new version for Oneiric will be up shortly, check the link in my sig or for more info go to the [project page]("http://andyduffell.com/techblog/?page_id=396") on my site.

---

### Post by Jose Catre-Vandis on 2011-09-07
> **Paqman said:**
> It always supports all currently supported versions of Ubuntu, so it will currently work on Lucid, Maverick and Natty. The new version for Oneiric will be up shortly, check the link in my sig or for more info go to the [project page]("http://andyduffell.com/techblog/?page_id=396") on my site.

Currently, the link in this thread doesn't include maverick and natty, only goes as far as Lucid, however the link on your project page for v.1.1.1 does :)

---

### Post by sisco311 on 2011-09-07
Didn't read the whole script by I have some of suggestions if you don't mind. :)

The syntax of if is:
```
if <COMMMANDS>
then
    <COMMANDS>
elif <COMMANDS>
then
    <COMMANDS>
elif ...
    ...
else
    ....    
fi
```

So you could do something like:
```
if grep "10.10" > /dev/null 2>&1 
then
    echo "10.10"
elif grep "11.10" > /dev/null 2>&1
    echo ...
else
    echo "can't detect version" >&2
    exit 1
fi
```

`COMMAND` is used in old-style command substitution. The $(COMMAND) syntax is recommended.

You should consistently use [[ .. ]] to test strings or files, (( .. )) to test numbers or arithmetics and ''if ..'' to test commands. Do **NOT** use [ .. ] in bash, **only** in sh.

Add more error checks, you have to handle the case when one of the commands fails.

Always QUOTE YOUR VARIABLES!

---

### Post by MG&amp;TL on 2011-09-07
Does your script download anything? Becuase I've never been able to configure my internet on a minimal install.

---

### Post by Paqman on 2011-09-08
> **MG&TL said:**
> Does your script download anything? Becuase I've never been able to configure my internet on a minimal install.

Yes, it downloads all the packages to install. Tbh, if your network adaptor doesn't work straight away then doing a minimal install is probably not the path of least resistance.

If you're using wifi you might want to plug straight into your router and make sure you select the "graphical package management tools" option in the script. Then once you're booted into a desktop you'll be able to use the Additional Drivers tool to get your wifi drivers.

---

### Post by Paqman on 2011-09-08
> **sisco311 said:**
> Didn't read the whole script by I have some of suggestions if you don't mind. :)


Don't mind at all. I don't really know anything about bash, I've just adapted someone else's script and hit it with a hammer until it worked.

> `COMMAND` is used in old-style command substitution. The $(COMMAND) syntax is recommended.

Sorry, I don't really understand what you mean here. Can you give an example?

> Do **NOT** use [ .. ] in bash, **only** in sh.

Any part9cular reason, or is it just a convention?

> Add more error checks, you have to handle the case when one of the commands fails.

Definitely a good idea, will do.

> 
Always QUOTE YOUR VARIABLES!

Can you give an example? I'm not sure what you mean.

---

### Post by Oxwivi on 2011-09-08
If I used the script on 11.04, will it install Unity or GNOME Session? I think you should add the option to ask which shell to install for Natty and Oneiric using the grep suggestions by sisco311. Oneiric can have three options (GNOME 2.3x can be installed on it, right?)

---

### Post by Paqman on 2011-09-08
> **Oxwivi said:**
> If I used the script on 11.04, will it install Unity or GNOME Session?

You can choose from several DE's, for 11.04 those would be:

[list]
[*]Ubuntu desktop (Unity)
[*]Gnome core
[*]Kubuntu desktop
[*]Xubuntu desktop
[*]XFCE4
[*]Lubuntu desktop
[*]LXDE
[*]Myth TV
[/list]

> 
I think you should add the option to ask which shell to install for Natty and Oneiric using the grep suggestions by sisco311. Oneiric can have three options (GNOME 2.3x can be installed on it, right?)

For Oneiric your Gnome options will be Unity and Gnome Shell. Gnome 2 is deprecated and there is no minimal Gnome package in the Oneiric repos as far as I can tell. That's a real shame IMO. They did the same to KDE a little while ago too.

If you want a Gnome 2 or gnome-core machine I'd suggest installing Lucid, as it'll be supported for another couple of years.

---

### Post by Oxwivi on 2011-09-08
By the way, me-menu, dependency of Unity and GNOME Session installs Gwibber, which is something minimal users may not want. Will you ignore it or hack workarounds? I'm hacking my way to Me Menu with --no-install-recommends apt-get flag and then installing the rest of the recommends by myself. :(

---

### Post by Paqman on 2011-09-08
> **Oxwivi said:**
> By the way, me-menu, dependency of Unity and GNOME Session installs Gwibber, which is something minimal users may not want. Will you ignore it or hack workarounds? I'm hacking my way to Me Menu with --no-install-recommends apt-get flag and then installing the rest of the recommends by myself. :(

Yep, aware of that. The script won't install me-menu on gnome-core (uses indicator-applet-session instead), but will if you go for the full-fat Gnome (ie: ubuntu-desktop).

---

### Post by nothingspecial on 2011-09-08
Sisco311 has been correcting me now for some time, due to this perhaps I can help

The old style of command substitution is this eg

```
for file in `find ./ -type f`
```

You are supposed to do this now

```
for f in $(find ./ -type f)
```

So where you have commands enclosed in backticks in your script, enclose them in () with a $ infront instead.

[[ is a new improved version of [

[[ will do everything that [ will do but not the other way round.

If you don't quote your variables spaces can break them

eg say I have a file called paqmans script in a directory and I want to put every file in that directory in a variable using ls......


[COLOR="Blue"]Yes I know this is wrong I'm just trying to keep it simple[/COLOR]

```

$ a=$(ls)
```

Then I want to copy all the files in that directory to my home folder.
```
$ cp $a ~
cp: cannot stat `paqmans': No such file or directory
cp: cannot stat `script': No such file or directory
```

bash splits at the spaces so the variable contains paqmans and script (which don't exist) instead of the single file.

if I did cp "$a" the space wouldn't matter


Now because your script works you may say well why does any of it matter. This is what I used to think. But after continual head bashing by Sisco I've come to see -

1. It's good practice for yourself
2. When you put stuff out in the wild so to speak, people use it and modify it to their own needs (as you have done). If you don't do it properly in the first place then unintended results can happen.

It's all explained (including why not to use a=$(ls) ) in detail here

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

Have a look at the pitfalls section also and the faqs

---

### Post by Paqman on 2011-09-08
> **nothingspecial said:**
> 
Now because your script works you may say well why does any of it matter. This is what I used to think. But after continual head bashing by his highness of bash I've come to see -

1. It's good practice for yourself
2. When you put stuff out in the wild so to speak, people use it and modify it to their own needs (as you have done). If you don't do it properly in the first place then unintended results can happen.


Cheers, that's all good practical info.

My point of view is that having it working isn't a bad place to start. It's a work in progress, not set in stone. It'll get better the more I learn. My main focus is on making sure it doesn't knacker anybody's system and installs the right stuff, but nice clean easy to maintain code would be a good thing too. It's a bit of a monstrosity right now.

---

### Post by Bodsda on 2011-09-08
I have a suggestion. Instead of having to sit through answering 'no' to most questions on the list, how about having a website that allows people to graphically select the apps they want, then that generates the install script which they can download and run. 
 
That would be something I would use on a regular basis. I wouldn't want to sit through that script every time I do an install, it would take longer than manually installing every package as and when I need it.
 
You could go further with this, perhaps a feature that someone can use on a fully configured machine that generates a script that installs all packages that differ between a minimal install and their full install. So they can rebuild their machine very quickly.
 
Good work though!
Bodsda

---

### Post by Paqman on 2011-09-08
> **Bodsda said:**
> I have a suggestion. Instead of having to sit through answering 'no' to most questions on the list, how about having a website that allows people to graphically select the apps they want, then that generates the install script which they can download and run.

Good idea, but for the sake of simplicity I've stuck with a script that can run on a minimal install itself.
 
> 
That would be something I would use on a regular basis. I wouldn't want to sit through that script every time I do an install, it would take longer than manually installing every package as and when I need it.


Well if you know the exact packages you need, then you don't really need the script anyway ;)
 
> 
You could go further with this, perhaps a feature that someone can use on a fully configured machine that generates a script that installs all packages that differ between a minimal install and their full install. So they can rebuild their machine very quickly.


Apt-clone could do this, surely? 

They're all good ideas, but sadly more work than I've got time for right now. If you built it, I'd probably use it myself.

---

### Post by MG&amp;TL on 2011-09-08
The thing about a fully configured machine...I tried 'remastersys backup' recently, and it works great. You leave it to chug for a bit, and then it spits out an iso of your system. Pretty cool if you have something just how you want and you want it on another machine

---

