---
title: "using different timezone"
date: 2019-10-29
forum: Ubuntu, Linux and OS Chat
---

### Post by crip720 on 2019-10-29
Just wondering if a person set a different timezone, than theirs during installation, would it mess up anything besides the time?  Is it just to have the right time for you?  Thanks for any answers to my random thoughts.

---

### Post by wildmanne39 on 2019-10-29
A long time ago it caused me issues installing apps from the repositories if I remember correctly.

Edit:

Now that I have thought more about it, I believe the issue was with the CMOS clock reporting the wrong time that caused my issue.

---

### Post by TheFu on 2019-10-29
> **crip720 said:**
> Just wondering if a person set a different timezone, than theirs during installation, would it mess up anything besides the time?  Is it just to have the right time for you?  Thanks for any answers to my random thoughts.

A proper Unix system knows UTC and internally represents everything using that.  The TZ environment variable is what controls how the time is displayed.  I simply change that in my ~/.bashrc file to control what timezone gets displayed when I travel. For example:
```
 
#export TZ='Europe/London'; 
#export TZ='Asia/Bangkok'; 
# export TZ='Asia/Seoul'; 
# export TZ='Asia/Kathmandu'; 
# export TZ='Europe/Amsterdam'; 
# export TZ='Africa/Johannesburg'; 
export TZ='America/New_York';

```
Just ensure the TZ you want active is uncommented.  Then logout and login again.

---

### Post by crip720 on 2019-10-29
So you are saying that if I on purpose set the wrong time zone, the only thing that would happen is that I might miss a favourite TV show.

---

### Post by uRock on 2019-10-29
> **crip720 said:**
> So you are saying that if I on purpose set the wrong time zone, the only thing that would happen is that I might miss a favourite TV show.

Yes. Selecting New York, instead of Seattle will only alter the clock.

---

### Post by TheFu on 2019-10-30
> **uRock said:**
> Yes. Selecting New York, instead of Seattle will only alter the clock.

It will alter the display of the time, not the actual time that the system knows.  UTC will not be altered at all, just by changing the TZ environment variable.  In fact, if you open 10 different terminals and set each to a different, valid, TZ, then run 'date' to get the current time, each will display that information for just the timezone based on the environment variable.  The actual system clock wont be touched.

---

### Post by uRock on 2019-10-30
> **TheFu said:**
> It will alter the display of the time, not the actual time that the system knows.  UTC will not be altered at all, just by changing the TZ environment variable.  In fact, if you open 10 different terminals and set each to a different, valid, TZ, then run 'date' to get the current time, each will display that information for just the timezone based on the environment variable.  The actual system clock wont be touched.

Yup. I've never paid any mind to the system clock. Just the one in the panel and the one showing in my Motion video clips.

---

