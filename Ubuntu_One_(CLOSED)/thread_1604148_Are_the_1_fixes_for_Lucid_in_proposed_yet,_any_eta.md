---
title: "Are the 1 fixes for Lucid in proposed yet, any eta?  Like waiting for Christmas."
date: 2010-10-23
forum: Ubuntu One (CLOSED)
---

### Post by MechaMechanism on 2010-10-23
Are the 1 fixes in proposed yet for 10.04?  I know that eta is a dangerous game, but any eta.  How long are proposed software for LTS in proposed?  It's driving me crazy, where so close now to having 1 working on Lucid finally.  But in my opinion, better to be safe than sorry for an LTS.  I'm using LTS for the next 3 years.  :biggrin:

---

### Post by duanedesign on 2010-10-23
The Ubuntu One Stable PPA now contains the Maverick version of Ubuntu One for use in Lucid. You can add it with the following commands:

```
sudo add-apt-repository ppa:ubuntuone/stable
```


```
sudo apt-get update; sudo apt-get upgrade
```

thanks,
duanedesign

---

### Post by MechaMechanism on 2010-10-23
> **duanedesign said:**
> The Ubuntu One Stable PPA now contains the Maverick version of Ubuntu One for use in Lucid. You can add it with the following commands:

```
sudo add-apt-repository ppa:ubuntuone/stable
``````
sudo apt-get update; sudo apt-get upgrade
```thanks,
duanedesign
Thank you.

---

### Post by NHclimber on 2010-10-25
> **duanedesign said:**
> The Ubuntu One Stable PPA now contains the Maverick version of Ubuntu One for use in Lucid. You can add it with the following commands:

```
sudo add-apt-repository ppa:ubuntuone/stable
``````
sudo apt-get update; sudo apt-get upgrade
```thanks,
duanedesign

It wasn't this simple for me. I had to purge and remove everything I could find before reinstalling desktopcouch and ubuntuone. Critically, that included the desktopcouch databases.

---

