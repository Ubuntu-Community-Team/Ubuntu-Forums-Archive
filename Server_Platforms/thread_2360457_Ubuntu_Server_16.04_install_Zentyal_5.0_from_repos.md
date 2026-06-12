---
title: "Ubuntu Server 16.04 install Zentyal 5.0 from repositories fails"
date: 2017-05-05
forum: Server Platforms
---

### Post by glug1012 on 2017-05-05
I'm not usually the sort that gets stumped, but this is driving me nuts. I've used Zentyal as server since it was called Ebox and was based on Ubuntu 8.04. I find it to be a very convenient and powerful distribution. I now have a server that I want to upgrade from Ubuntu 12.04 (I plan on performing a clean install), but I'm running into issues with installing Zentyal. Namely that it doesn't work in any of my test systems.

The story thus far:

[LIST]
[*]I started with a clean Ubuntu 16.04 server install. (no gui)
[*]I followed the instructions listed here to add the repository for Zentyal 5.0: [https://wiki.zentyal.org/wiki/Installation_Guide](https://wiki.zentyal.org/wiki/Installation_Guide)
[*]I type in the magic command: sudo apt-get install zentyal
[*]And this is the result:
```
The following packages have unmet dependencies: zentyal : Depends: zentyal-core but it is not going to be installed
           Depends: zentyal-software but it is not installable
E: Unable to correct problems, you have held broken packages.
```
[*]I tried typing in: sudo apt-get install zentyal-core
[*]Result:
```
The following packages have unmet dependencies: zentyal-core : Depends: libhtml-mason-perl (>= 1:1.56+zentyal1-1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```
[*]Installing libhtml-mason-perl manually installs version 1:1.56, but installing zentyal-core still gives me the same error message.
[/LIST]

I've tried installing previous version through repositories, but I get similar error messages. I've attempted installing from an iso on Zentyals site and the Zenbuntu gui loads fine, but the zentyal-core package doesn't install properly. My target machine is 32-bit, but I've attempted this on multiple physical computers and virtual machines, both in 32-bit and 64-bit. Still getting the same issue.

I'm completely flummoxed. Is Zentyal just in a completely broken state right now? 

Is anybody on here been able to install Zentyal successfully within the last few months?

Thanks in advanced!

---

