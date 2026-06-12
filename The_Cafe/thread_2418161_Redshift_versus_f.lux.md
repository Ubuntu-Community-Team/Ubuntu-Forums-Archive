---
title: "Redshift versus f.lux"
date: 2019-05-02
forum: The Cafe
---

### Post by deanr2 on 2019-05-02
Redhsift seems to be suffering from issues with geoplus recently. Mine stops and starts on a random basis and the workaround involving changing the config files, which is a recent post on the mint forums, didn't work. Instead I discovered and installed f.lux. Is anyone familiar with this program? Apart from putting in your location manually, which solves the problems redshift seems to currently be undergoing, are there any pros or cons to one or the other?

Thanks.

---

### Post by ajgreeny on 2019-05-02
The command **redshift -l list** will show the available location providers.

Here's what I get from that, showing that geoclue2 is one of them, or manually setting location in the redshift.conf file in ~/.config
```
redshift -l list
Available location providers:
  geoclue2
  manual
```
Make the change to your redshift.conf file, replacing geoclue with geoclue2 and see if that helps.
Redshift seems to be working as it should in my systems.

[COLOR="#FF0000"]EDIT:[/COLOR]
Ignore this post; I see that I have the location set manually, and if I remove that from the redshift.conf file the application fails, just as you said.

---

### Post by deanr2 on 2019-05-03
Thanks for the reply @ajgreeny

I get the same output when I type redshift -l list into the terminal. 

Redshift appears to be working this morning on first boot-up but I expect, like yesterday, it won't be working by the afternoon and the location will change to 0.0 and 0.0 again.

Anyway, what about f.lux. Any experience with that?

---

### Post by ajgreeny on 2019-05-03
None, I'm afraid.

I will look into it and see if it's any better than redshift, though redshift fits my needs when it's manually set to location, as I do not usually take any computer overseas with different time zones.

---

### Post by kc1di on 2019-05-03
Not sure about redshift , It worked for me when I last tried it.  But this[ pages tells you how to use f.flux-gui from PPA.]("https://itsfoss.com/night-shift-flux-ubuntu-linux/") and it's was working last time I tried it also.
I now use gnome and it has a built in night light feature.

---

### Post by deanr2 on 2019-05-03
Thanks for the link. I'm running f.lux now and it seems to work and is nice and easy to configure. Hopefully some others will find it of use - even if they don't encounter the problems with redshift I and many others seem to have encountered. Always good to know software alternatives I guess :)

By the way, if I may, how do I create an @name in a post that is 'live' and what is it actually called? I've been searching online all morning and can't find anything of any help :(

---

### Post by deanr2 on 2019-05-03
> **ajgreeny said:**
> None, I'm afraid.

I will look into it and see if it's any better than redshift, though redshift fits my needs when it's manually set to location, as I do not usually take any computer overseas with different time zones.

Thanks ajgreeny. Much appreciated.

---

### Post by ajgreeny on 2019-05-11
I have just managed to find the way to enable geoclue2 in redshift thanks to a query at [https://askubuntu.com/questions/968872/redshift-can-not-find-geoclude2-after-ubuntu-17-update](https://askubuntu.com/questions/968872/redshift-can-not-find-geoclude2-after-ubuntu-17-update)

I have just made the changes shown below in that askubuntu page to my **/etc/geoclue/geoclue.conf** file.

Following that quit redshift and then
[LIST=1]
[*]Add geoclue2 to the ~/.config/redshift.conf file and comment out with ; the lat & lon lines.
[*]Add the following to /etc/geoclue.conf file
[/LIST]

```
[redshift]
allowed=true
system=false
users=
```

Now restart redshift and it should work whatever your location.

---

