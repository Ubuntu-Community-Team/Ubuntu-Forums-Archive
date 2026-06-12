---
title: "TIP: Kubuntu 11.04 64-bit faster Flash Player"
date: 2011-05-06
forum: Tutorials
---

### Post by slooksterpsv on 2011-05-06
So I came across this tip on the Kubuntu Forums regarding 64-bit Kubuntu and Flash. This has actually made flash on my system speed up by 200%. Do the following:

```

sudo apt-add-repository ppa:sevenmachines/flash && sudo apt-get update && sudo apt-get install flashplugin64-installer

```

Close all Firefox windows, open them back up, and test it out.

---

### Post by mj360 on 2011-08-27
thanks for the thread, my flash wasn't even working. but thanks to you, it's working great.

---

### Post by Sladex on 2011-08-29
god bless u, Ive had looking  a solution for 3 hours because 64 bit flash does not work easily.

thank you :P

---

### Post by andrei90 on 2011-08-30
Very interesting. Thank you for the tips.

---

### Post by siabost on 2011-09-04
Works a treat!

Thanks.

I had the "official" 64bit Flash included with the kubuntu-restricted-extras/addons package running in 64bit Kubuntu on two machines for a while only to have it stop working for no apparent reason although still installed. I had been getting round it with Gnash but this works better.

Anyone know why?

Thanks again. :P

---

### Post by MountainX on 2012-03-15
> **slooksterpsv said:**
> So I came across this tip on the Kubuntu Forums regarding 64-bit Kubuntu and Flash. This has actually made flash on my system speed up by 200%. Do the following:

```

sudo apt-add-repository ppa:sevenmachines/flash && sudo apt-get update && sudo apt-get install flashplugin64-installer

```Close all Firefox windows, open them back up, and test it out.

sevenmachines PPPA has been removed. 

It is no longer necessary to manually install flash. The package adobe-flashplugin will install the latest version of flash (currently 11).

---

