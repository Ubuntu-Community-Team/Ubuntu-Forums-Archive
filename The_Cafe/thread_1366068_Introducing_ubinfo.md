---
title: "Introducing ubinfo"
date: 2009-12-28
forum: The Cafe
---

### Post by Dj Melik on 2009-12-28
Ubinfo is a very simple python script. It basically just outputs the 'Ubuntu' logo along with very basic information regarding the system. 

Example: [http://omploader.org/vMzNsdg](http://omploader.org/vMzNsdg)
Example2: [http://imagebin.org/77166](http://imagebin.org/77166)

Ubinfo comes in two flavors at the moment: ubinfo(Ubuntu) and kubinfo(Kubuntu). 

Download links:

Ubuntu: [http://github.com/djmelik/ubuntu/blob/master/ubinfo.py](http://github.com/djmelik/ubuntu/blob/master/ubinfo.py)
Kubuntu: [http://github.com/djmelik/ubuntu/blob/master/kubinfo.py](http://github.com/djmelik/ubuntu/blob/master/kubinfo.py)

There is really no difference between the scripts except the color scheme :P; i will converge them into 1 script eventually.

To run the script: 

1) Download the script from the link presented above.
2) Open a terminal.
3) Navigate to where the script is located.
4) Run: '**python ubinfo.py**' or '**python kubinfo.py**' depending on which one you have.

To customize the script to your needs (disabling and enabling the data that is outputed): merely, edit the script and look for the "# Display" array (its near the top). Proceed by uncommenting and commenting the array elements to your needs. Note: You can only display a total of 13 fields so far.

To take a screenshot (requires the package: 'scrot'): Just add an option "-s" whenever executing the script.

If you run into any bugs, please post the error messages, so that I may fix and improve the script. Also looking forward to suggestions.

---

### Post by witeshark17 on 2009-12-28
Have to take a look at this... :popcorn:

---

### Post by phrostbyte on 2009-12-28
Nice!

I changed os_display to this:

```
def os_display(): 
	os = Popen(['lsb_release', '-d'], stdout=PIPE).communicate()[0].split()[1::]
	output('OS', '%s %s' % (os[0], os[1]))
```

---

### Post by Dj Melik on 2009-12-28
> **phrostbyte said:**
> Nice!

I changed os_display to this:

```
def os_display(): 
	os = Popen(['lsb_release', '-d'], stdout=PIPE).communicate()[0].split()[1::]
	output('OS', '%s %s' % (os[0], os[1]))
```
Thanks! I pushed your code to github.
```

def os_display(): 
	arch = Popen(['uname', '-m'], stdout=PIPE).communicate()[0].rstrip('\n')
	distro = Popen(['lsb_release', '-d'], stdout=PIPE).communicate()[0].split()[1::]
	os = '%s %s %s' % (distro[0], distro[1], arch)
	output('OS', os)
```

:D

---

### Post by OneIdle on 2009-12-28
looks nice!


Suggestion: add Load Average

---

### Post by ibuclaw on 2009-12-28
Hmm... this looks like something you could add to the login message - or any time you open a terminal (add it's execution to ~/.bashrc).

---

### Post by phrostbyte on 2009-12-28
[http://github.com/phrostbyte/ubuntu](http://github.com/phrostbyte/ubuntu)

I made some improvements. I think you can merge it into your branch, but I'm a newb with git. :)

I think it will be smart to have a shared python script (instead of two) because a lot of the functionality in either is similar, and that will simplify development.

Or perhaps one "library" and two "frontends".

---

### Post by OneIdle on 2009-12-28
> **tinivole said:**
> Hmm... this looks like something you could add to the login message - or any time you open a terminal (add it's execution to ~/.bashrc).

Could you provide an example as to how to add to ~/.bashrc ?

Figured it out!

edit ~/.bashrc
```
**gksudo gedit ~/.bashrc**
```

add a line similar to the following
```
**cd Desktop && python ubinfo.py**
``` change Desktop to wherever you saved your .py to.
save.
open terminal.

---

### Post by Dj Melik on 2009-12-28
> **phrostbyte said:**
> [http://github.com/phrostbyte/ubuntu](http://github.com/phrostbyte/ubuntu)

I made some improvements. I think you can merge it into your branch, but I'm a newb with git. :)

I think it will be smart to have a shared python script (instead of two) because a lot of the functionality in either is similar, and that will simplify development.

Or perhaps one "library" and two "frontends".

I'm a newb at git as well :) I read about it, you have to click on pull request and click my name.

BTW, do you use IRC?

---

### Post by Dj Melik on 2009-12-28
> **OneIdle said:**
> Could you provide an example as to how to add to ~/.bashrc ?

Figured it out!

edit ~/.bashrc
```
**gksudo gedit ~/.bashrc**
```

add a line similar to the following
```
**cd Desktop && python ubinfo.py**
``` change Desktop to wherever you saved your .py to.
save.
open terminal.

or you can just do

```
python ~/whereyousavedthescript/ubinfo.py
```

---

### Post by phrostbyte on 2009-12-28
[IMG]http://img97.imageshack.us/img97/2175/ssubuntuinfo.png[/IMG]

Changes should be in git. :)

---

### Post by phrostbyte on 2009-12-28
> **Dj Melik said:**
> I'm a newb at git as well :) I read about it, you have to click on pull request and click my name.

BTW, do you use IRC?

Yes, I am on IRC regularly (although not now) in the channel ##club-ubuntu on freenode.


I think the command is indeed "git pull <repo>"

:)

---

### Post by phrostbyte on 2009-12-28
There has to be some better way to add stuff to the format string without screwing up colors.

---

### Post by Dj Melik on 2009-12-28
> **phrostbyte said:**
> There has to be some better way to add stuff to the format string without screwing up colors.

[http://github.com/djmelik/archey/blob/master/archey](http://github.com/djmelik/archey/blob/master/archey)
Take a look at my arch linux version.

also try to get on IRC, i'd like to talk :)

---

### Post by Xbehave on 2009-12-28
I have an environmental variable called DESKTOP_SESSION, will that be more/same/less right than your current method?

well as an alternative method (for when your current method fails) you could add

```
from os import environ
if environ.has_key("DESKTOP_SESSION"): de=environ["DESKTOP_SESSION"]
```
the formating will not always be right though so you may want to add
```
from os import environ
if environ.has_key("DESKTOP_SESSION"):
    de=environ["DESKTOP_SESSION"]
    case_dict = {'gnome': 'GNOME', 'kde': 'KDE'}
    if case_dict.has_key(de):
         de=environ[de]
    else:
         de=de.title() 
```

Anyway nice script, feel free to ignore my advice as it may be silly/wrong.

---

### Post by Dj Melik on 2009-12-28
Phrostbyte, there must be a better way to grab CPU info.. because it doesn't stay consistent all throughout.

[http://omploader.org/vMzNzYw](http://omploader.org/vMzNzYw)

---

### Post by phrostbyte on 2009-12-28
> **Dj Melik said:**
> Phrostbyte, there must be a better way to grab CPU info.. because it doesn't stay consistent all throughout.

[http://omploader.org/vMzNzYw](http://omploader.org/vMzNzYw)

I do not know of any other way.

---

### Post by ibuclaw on 2009-12-29
> **OneIdle said:**
> Could you provide an example as to how to add to ~/.bashrc ?

Figured it out!

edit ~/.bashrc
```
**gksudo gedit ~/.bashrc**
```

add a line similar to the following
```
**cd Desktop && python ubinfo.py**
``` change Desktop to wherever you saved your .py to.
save.
open terminal.
Two flaws I want to point out

1) **Never** use gksudo on **files owned by you**!!!

A simple
```
gedit ~/.bashrc
```
will do.

2) There is no file checking in your code example.
A better solution would be to install the app.
```
sudo install ubinfo.py /usr/local/bin
```

Then at the bottom of .bashrc, put in
```

UBINFO="`which ubinfo.py`"
if [ -n "$UBINFO" -a -x "$UBINFO" ]; then
    "$UBINFO"
fi

```

Regards
Iain

---

### Post by OneIdle on 2009-12-31
> **tinivole said:**
> Two flaws I want to point out

1) **Never** use gksudo on **files owned by you**!!!

A simple
```
gedit ~/.bashrc
```
will do.

2) There is no file checking in your code example.
A better solution would be to install the app.
```
sudo install ubinfo.py /usr/local/bin
```

Then at the bottom of .bashrc, put in
```

UBINFO="`which ubinfo.py`"
if [ -n "$UBINFO" -a -x "$UBINFO" ]; then
    "$UBINFO"
fi

```

Regards
Iain

Thanks for the info.

---

