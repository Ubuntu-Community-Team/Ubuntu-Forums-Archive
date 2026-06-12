---
title: "Which lens do you use?"
date: 2012-09-07
forum: The Cafe
---

### Post by Petro Dawg on 2012-09-07
I've been using Ubuntu for about a year now and never knew what a Unity lens was until a couple days ago (yup, that's how much I pay attention).  I expect new lenses are coming out all the time and I wanted to start a thread that would keep people informed of new lenses as they are being released.  Post your favorite lens and the installation method.  

Add a screen shot if you wish (thumbnail with link for the people with slower connections speeds please)

I'll get things started...

I'm running Ubuntu12.04(2D)
I don't think its very new but I installed the wikipedia lens which allows searching wikipedia directly from the dash and I think it is rather nifty.

[[IMG]http://farm9.staticflickr.com/8315/7953000796_a85556b69d_n.jpg[/IMG]]("http://farm9.staticflickr.com/8315/7953000796_a85556b69d_b.jpg") 

Installed by running this in terminal...

```
sudo add-apt-repository ppa:scopes-packagers/ppa 
sudo apt-get update
sudo apt-get install unity-lens-wikipedia
```

---

### Post by Primefalcon on 2012-09-07
I use 2

wikipedia lens
runescape wiki lens


rs wikia lens
```
sudo add-apt-repository ppa:ryanmichaelmcclure/ppa; sudo apt-get update && sudo apt-get install unity-lens-runescapewikia
```

---

### Post by Mikeb85 on 2012-09-08
I use a stock ticker lens, the cities lens, the cooking lens, and the wikipedia lens...

---

### Post by Petro Dawg on 2012-09-08
> **Mikeb85 said:**
> I use a stock ticker lens, the cities lens, the cooking lens, and the wikipedia lens...

Is there something you have to do to get the cooking lens to work?  I tried installing it on my wife's computer and the lens would never return any results, just remained blank.  I uninstalled, reinstalled, rebooted, with no luck in getting it to work.  She's running Ubuntu 12.04-2D.

---

### Post by Frogs Hair on 2012-09-08
I use the stock and news so far. [http://www.iloveubuntu.net/easy-guide-ubuntu-1204s-unity-lenses](http://www.iloveubuntu.net/easy-guide-ubuntu-1204s-unity-lenses)

---

### Post by Frogs Hair on 2012-09-08
> **Petro Dawg said:**
> Is there something you have to do to get the cooking lens to work?  I tried installing it on my wife's computer and the lens would never return any results, just remained blank.  I uninstalled, reinstalled, rebooted, with no luck in getting it to work.  She's running Ubuntu 12.04-2D.

After installing the cooking lens and  looking in the folder usr/share/unity I think the problem may have to do with setting a locale. There is an email address for the developer in file contents.

---

### Post by Petro Dawg on 2012-09-08
> **Frogs Hair said:**
> After installing the cooking lens and  looking in the folder usr/share/unity I think the problem may have to do with setting a locale. There is an email address for the developer in file contents.

I installed the cooking lens on my computer and have the same results (or lack of results)...

[[IMG]http://farm9.staticflickr.com/8182/7955679278_74452e0527_n.jpg[/IMG]]("http://farm9.staticflickr.com/8182/7955679278_74452e0527_b.jpg")

Thanks for the suggestion Frogs_Hair, however I'm not sure what you mean by setting a locale.  I'm kinda a newbie to Linux and a total Noob when it comes to lenses.

This is the contents of usr/share/unity/lenses/cooking...

[[IMG]http://farm9.staticflickr.com/8310/7955716858_44e60dd147_n.jpg[/IMG]]("http://farm9.staticflickr.com/8310/7955716858_44e60dd147_b.jpg")

What do I add/edit here?  Am I even looking in the right place?

---

### Post by Frogs Hair on 2012-09-08
This is the part I am wondering about. ```
# See if we use a German locale
lang = locale.getdefaultlocale()[0]
if '_' in lang:

```

---

### Post by exploder on 2012-09-08
Great thread and a terrific idea! Thanks for getting this going.

---

### Post by Petro Dawg on 2012-09-08
> **Frogs Hair said:**
> This is the part I am wondering about. ```
# See if we use a German locale
lang = locale.getdefaultlocale()[0]
if '_' in lang:

```


In the unity-lens-cooking file this is the code...
```
# See if we use a German locale
lang = locale.getdefaultlocale()[0]
if '_' in lang:
    lang = lang.split('_', 1)[0]
if lang == 'de':
    COOKSUNITED = "Chefkoch Rezepte"
else:
    COOKSUNITED = _("Cooksunited Recipes")
```

In the unity-scope-cooksunited file this is the code...
```
    # Check if we are running in a German locale. Otherwise, the results are
    # rather useless, so don't create the daemon.
    global lang
    lang = locale.getdefaultlocale()[0]
    if '_' in lang:
        lang = lang.split('_', 1)[0]
        baseurl = "http://www.cooksunited.co.uk/rs/scr/s0/%s/recipes.html"
        if lang == 'de':
                baseurl = "http://www.chefkoch.de/rs/s0/%s/Rezepte.html"
        if lang == 'nl':
                baseurl = "http://www.cooksunited.nl/rs/scr/s0/%s/recepten.html"
```

Looks the same as yours to me.  :confused:

---

