---
title: "Which version - 64 bit or 32?"
date: 2012-02-27
forum: Server Platforms
---

### Post by iangarforth on 2012-02-27
I will be deploying a small thin client network on quite an old server, whose chip is an AMD64 3000+.  Does the 64 signify I should be installing the 64 bit version of the OS, or should I use the 32 bit version?

---

### Post by hawkmage on 2012-02-27
I have a tendency to install 64 bit on hardware that supports it but that is a personal preference that may not always be the best choice.  

There are a number of 64 bit capable systems that I have run 32 bit Linux on because of specific requirements for what that system is going to need to run. 

My first criteria would be how much memory does the system have and to how much memory does any one process need?  If any one process will need more than about 2.5 GB of ram you should look at using the 64 bit version.  If the system only has 4 GB or less of RAM then the 32 bit version will work for you.

Next you need to determine what your applications you will be running on the system.  Are there any that are not part of what is provided with the Linux distribution. If everything you will be using is part of the distribution then you are free to go either 32 or 64 but if there are any that are not part of the distribution then you should look at what they require.  If you have something that you need to run that is only 32 bit then that is your answer.  However you can include 32 bit app support in 64 Linux that can eliminate this "requirement" in most situations.  

Another thing to be aware of is that if you are going to be downloading, building and installing Open Source apps via tarballs not app of the configure/make scripts that come with them work with 64 bit using the same configuration/make options as a 32 bit builds.

There are many other little things that can push you one way or another but those are my initial thoughts.

---

