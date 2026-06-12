---
title: "base files in for artful"
date: 2017-04-21
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-04-21
Away we go ! :)

```

ventrical@ventrical-MS-7850:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Artful Aardvark (development branch)
Release:    17.10
Codename:    artful
ventrical@ventrical-MS-7850:~$ 

```

---

### Post by wildmanne39 on 2017-04-24
I was thinking I would help test 17.10, from what I have read I can only upgrade from 17.04 right now and not do a clean install is that correct? I want to keep 17.04 and put 17.10 on a different partition.
Thanks

---

### Post by ventrical on 2017-04-24
> **wildmanne39 said:**
> I was thinking I would help test 17.10, from what I have read I can only upgrade from 17.04 right now and not do a clean install is that correct? I want to keep 17.04 and put 17.10 on a different partition.
Thanks

Just do a fresh install of 17.04. It will ask lf you if you want to install 17.04 alongside 17.04. Yes. It will auto partition for you , or you can use the slider or you can use 'something else'. Once you install the new fresh install on the new partition you can choose the new install from the grub menu.

Then go into terminal and:

```

sudo sed -i 's/zesty/artful/g' /etc/apt/sources.list

```

then

```


sudo apt-get update && sudo apt-get dist-upgrade


```

then

```

sudo apt-get update

sudo apt-get dist-upgrade

```

When you type in:

```

lsb_release -a

```

it will come up 17.10 and just keep updating from there until release day.

Regards..

arrgh.. sorry about fonts - again! :)

---

### Post by wildmanne39 on 2017-04-24
Thanks for the detail directions, I was thinking that I would have to install 17.04 to a new partition and then upgrade to 17.10 but it is nice to have it confirmed and to have the directions in one place.

I will install tomorrow, it is getting late here tonight.:)

---

### Post by ventrical on 2017-04-24
Just as an add-on, don't forget:

[https://wiki.ubuntu.com/U+1/tester-wiki#New_Beta_Testers_Warnings](https://wiki.ubuntu.com/U+1/tester-wiki#New_Beta_Testers_Warnings)

I have several different hardware formfactors so I will often test a development version alongside a release version. I have not had to many problems so far but I always like to keep my working installs seperate from development installs hence extra hdds.

Regards..

---

