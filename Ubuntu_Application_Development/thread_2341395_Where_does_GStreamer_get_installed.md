---
title: "Where does GStreamer get installed"
date: 2016-10-27
forum: Ubuntu Application Development
---

### Post by rickblacker on 2016-10-27
I know it's installed in some capacity or another on my machine. 
When I run dpkg -l | grep gstreamer, I get back a list of packages.
When I run apt-cache search gstreamer i get back a bunch of results

But, I have not figured out yet now to find where the headers and libraries are physically located.
I've manually looked in 
/usr/lib
/usr/include

Nothing... There is nothing in them.

I've looked in 
/usr/local/lib
/user/local/include

Nothing there either. 

The reason i'm asking is because I've tried and MISERABLY failed at trying to create the utmost basic GStreamer project in QT Creator using CMake.  So, I'd like to go back to using Eclipse where I can specify the location of the headers and libraries. But, I can't find them....

Any help will be appreciated beyond imagination.

---

### Post by howefield on 2016-10-28
Not sure if it helps, but try 

```
dpkg -c path/to/package/filename
```

---

### Post by vasa1 on 2016-10-28
```
locate gstreamer
```will give you some clues.

---

