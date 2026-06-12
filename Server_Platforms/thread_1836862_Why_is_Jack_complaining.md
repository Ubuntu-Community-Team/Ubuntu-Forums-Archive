---
title: "Why is Jack complaining?"
date: 2011-08-31
forum: Server Platforms
---

### Post by jeffbarish on 2011-08-31
Sound is working perfectly on my Ubuntu Server platform -- except that I continually get the messages:

Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

I see reports from frustrated individuals who are trying to get sound to work but are getting this error message and no sound.  However, I believe that I am using alsa (with gstreamer), so I never installed any of jack or tried to get it to run.  Obviously, something from jack must have come by default with Ubuntu Server. In fact, I have found that the package libjack-jackd2-0 is installed.  Could that be where this message is coming from?  Should I uninstall libjack-jackd2-0?  I am reluctant to make changes like that because sound is working, but it would be nice if I were able to get rid of this error message.  To emphasize, I am not interested in installing Jack as sound is working, only in ending the nagging.

---

