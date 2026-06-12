---
title: "Dash not working after distribution upgrade (through sources.list)"
date: 2014-01-17
forum: Ubuntu Development Version
---

### Post by NikTh on 2014-01-17
Ok, I made the "big step" and I upgraded from Ubuntu 13.04 to 14.04 directly through /etc/apt/sources.list file. Big upgrade procedure here as I have too many packages in this installation (dev packages and 5 different DEs= Unity,GNOME,Lubuntu-desktop,Cairo-Dock,KDE). 

Here is a log file for anyone who wants to see &#8594; [http://pastebin.com/raw.php?i=kakRAier](http://pastebin.com/raw.php?i=kakRAier)

Now, the only significant  problem  here is the Dash from Unity DE. Does not contain any lenses and the search function doesn't work , neither local or Web. 

What I have tried is 

1) Reset Unity(with the known commands) and revert to original configuration settings with ```
rm -rf .compiz* .gconf* .config/dconf/ .config/compiz*
```
2) Reinstall unity and related unity-lens packages. 

Do you have any other suggestions ? 

Tip that might help, during the upgrade I had multiple questions about several configuration files , but I selected the default option which is N(o), that is, "do not replace the config file with the newer one, but keep the old".

---

### Post by Mateusz Stachowski on 2014-01-17
> **NikTh said:**
> 
Tip that might help, during the upgrade I had multiple questions about several configuration files , but I selected the default option which is N(o), that is, "do not replace the config file with the newer one, but keep the old".

That might be the source of the problem. There were new unity packages installed and old replaced. I think that it's better to replace old configs.

Anyway the first thing that I would try is to reset unity with unity-tweak-tool.

[http://askubuntu.com/questions/17610/how-do-i-reset-my-unity-configuration](http://askubuntu.com/questions/17610/how-do-i-reset-my-unity-configuration)

```
sudo apt-get install unity-tweak-tool
unity-tweak-tool --reset-unity
```

If that didn't help then try reinstalling unity-scope-home.

```
sudo apt-get install --reinstall unity-scope-home
```

Next in line of usual Dash is not working solutions are:

```
rm ~/.cache/software-center -R
unity-tweak-tool --reset-unity
```

```
rm -rf ~/.local/share/zeitgeist
```

Then logout and login back.

Also you could look at the contents of your ~/.xsession-errors for some insight what's crashing.

Some people also used this:

```
sudo updatedb
```

---

### Post by ventrical on 2014-01-17
> **NikTh said:**
> Ok, I made the "big step" and I upgraded from Ubuntu 13.04 to 14.04 directly through /etc/apt/sources.list file. Big upgrade procedure here as I have too many packages in this installation (dev packages and 5 different DEs= Unity,GNOME,Lubuntu-desktop,Cairo-Dock,KDE). 

Here is a log file for anyone who wants to see &#8594; [http://pastebin.com/raw.php?i=kakRAier](http://pastebin.com/raw.php?i=kakRAier)

Now, the only significant  problem  here is the Dash from Unity DE. Does not contain any lenses and the search function doesn't work , neither local or Web. 

What I have tried is 

1) Reset Unity(with the known commands) and revert to original configuration settings with ```
rm -rf .compiz* .gconf* .config/dconf/ .config/compiz*
```
2) Reinstall unity and related unity-lens packages. 

Do you have any other suggestions ? 

Tip that might help, during the upgrade I had multiple questions about several configuration files , but I selected the default option which is N(o), that is, "do not replace the config file with the newer one, but keep the old".
With all those DEs it could be something in your lightdm.conf file that is not jibing and on a few occasions I would choose 'yes' when prompted to change config files with no ill effects.

---

### Post by NikTh on 2014-01-17
Ok, that was easy enough.. haha 

```
sudo apt-get install --reinstall unity-scope-home #this also pulled some other two packages
```

everything is up and running again :)

---

