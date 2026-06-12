---
title: "DPKG: Unrecoverable fatal error, Missing final line in 'libkrb5support0:amd64'"
date: 2017-05-29
forum: Server Platforms
---

### Post by keilerkopf on 2017-05-29
[SIZE=2][FONT=arial]Hi,
first of all I have to mention that I have low experience by using raspberrys and im not really into linux but have now the task to set up a small server with [/FONT][/SIZE][COLOR=#333333][FONT=arial]16.04.2 LTS (Xenial Xerus) amd64. I installed the System on a NISE 50C with an o[/FONT][/COLOR]nboard Intel® Atom™ processor E3826 dual core, 1.46GHz. Setting up the System worked. But when I want to use "sudo apt-get update" and afterwards "sudo apt-get upgrade" I recived an error message. Here is an example:

So when using sudo apt-get upgrade console says:[INDENT][FONT=courier new]Preconfiguring packages ...
dkpg: unrecoverable fatal error, aborting:
file list file for package 'libkrb5support0:amd62' is missing final newline
E: sub-process /usr/bin/dpkg returned an error code (2) [/FONT][/INDENT]

The error message is not always the same. I experienced several other packages that won't run like 'libheimatlm0-heimdal' or 'wget'. After reinstalling I have other messages. I also tried 14.04.5. The result was the same.
[COLOR=#333333][FONT=arial]
Thankful for help
Alexander

[/FONT][/COLOR]

---

### Post by keilerkopf on 2017-05-29
When I try to install a package afterwards e.g. [FONT=courier new]sudo apt-get install libssl-dev[/FONT] I recive the same error message.

Kind regards
Alexander

---

### Post by keilerkopf on 2017-05-30
Are there any hints or suggestions? Is this the right forum?

---

### Post by darkod on 2017-05-30
Did you have internet during the installation? I have noticed that sometimes apt can be misconfigured if there is no internet during installation because it tries to download packages even during the install.

Also what you can try is repair apt and finish configuration of any pending packages. If I'm not mistaken the commands were:
```
sudo apt-get install -f
sudo dpkg --configure -a
```

The error message is always about the same package (libkrb5support0), or if you try installing a package then its name will be in the error message? If it is always the same package it might have gotten corrupted and maybe remove/purge will help get rid of it. But try the above commands first and see what they say.

---

### Post by keilerkopf on 2017-05-30
[FONT=arial]During Installation the Internet is constant on. I'm here in a company with direct connection to our infrastructure. Previosly I configrued a lot of Raspberrys with no problem concerning the inetconnection.
[/FONT]
When I perform ```
[FONT=courier new]sudo apt-get update[/FONT] 
```and afterwards ```
[FONT=courier new]sudo apt-get[/FONT] [FONT=courier new]upgrade [/FONT]
```then the result is 
```

[FONT=arial][COLOR=#000000]Preconfiguring packages ...[/COLOR]
[COLOR=#000000]dkpg: unrecoverable fatal error, aborting:[/COLOR]
[COLOR=#000000]file list file for package 'libkrb5support0:amd62' is missing final newline[/COLOR]
[/FONT][COLOR=#000000][FONT=&amp][FONT=arial]E: sub-process /usr/bin/dpkg returned an error code (2)[/FONT]
[/FONT][/COLOR]
```
[FONT=arial]After that I just wanted for testing to install the libssl-dev with [/FONT][FONT=courier new]```
[COLOR=#000000]s[/COLOR][COLOR=#000000]udo apt-get install libssl-dev[/COLOR]
```[COLOR=#000000] [FONT=arial]and the terminal gave the same error message as mentioned above.

That was the the situation yesterday and after a reinstall that I did today... same error message.

So I did 
[/FONT][/COLOR][/FONT]```
[COLOR=#000000][FONT=&amp]sudo apt-get install -f[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]sudo dpkg --configure -a[/FONT][/COLOR]
```[FONT=courier new][COLOR=#000000][FONT=arial]

The result is
[/FONT][/COLOR][/FONT]```
[FONT=&amp][COLOR=#000000]Extracting templates from packages: 100%
Preconfiguring packages ...[/COLOR]
[COLOR=#000000]dkpg: unrecoverable fatal error, aborting:[/COLOR]
[/FONT][COLOR=#000000][FONT=&amp]E: sub-process /usr/bin/dpkg returned an error code (2)[/FONT][/COLOR][FONT=courier new][COLOR=#000000][FONT=arial]
[/FONT][/COLOR][/FONT]
```[FONT=courier new][COLOR=#000000][FONT=arial]

So the former error with the new line issue is gone, but still it won't work.

Thx for help.[/FONT][/COLOR][/FONT]

---

### Post by darkod on 2017-05-30
If you did a reinstall and still the same issue, I would try downloading the ISO again, and then making new cd/usb and try again. It might be some corruption in the download or when making the install media, although that's a rare situation. But it can happen.

I have installed plenty of ubuntu servers, mostly virtual machines, and it never happened to me apt-get to be broken right after new installation.

---

### Post by keilerkopf on 2017-05-31
I followed the instructions gaven under
[https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

wrote a new image to my usb stick, installed the system and still having the same error
[FONT=arial][COLOR=#000000]```
Preconfiguring packages ...[/COLOR]
[COLOR=#000000]dkpg: unrecoverable fatal error, aborting:[/COLOR]
[COLOR=#000000]file list file for package 'libkrb5support0:amd62' is missing final newline[/COLOR]
[/FONT][COLOR=#000000][FONT=arial]E: sub-process /usr/bin/dpkg returned an error code (2)[/FONT][/COLOR]
```
](*,)

---

### Post by keilerkopf on 2017-05-31
The image I use is appropriate to the hardware I use nor?

---

### Post by keilerkopf on 2017-05-31
I replaced the server with another one. It's still a [COLOR=#333333][FONT=arial]NISE 50C with an o[/FONT][/COLOR][COLOR=#000000]nboard Intel® Atom&#8482; processor E3826 dual core, 1.46GHz.

Now I am having another error
[/COLOR]```
[FONT=arial][COLOR=#000000]Preconfiguring packages ...[/COLOR]
[COLOR=#000000]dkpg: unrecoverable fatal error, aborting:[/COLOR]
[COLOR=#000000]file list file for package 'libsasl2-modules' is missing final newline[/COLOR]
[/FONT][COLOR=#000000][FONT=arial]E: sub-process /usr/bin/dpkg returned an error code (2)[/FONT][/COLOR]
```[COLOR=#000000]
[/COLOR]

---

### Post by darkod on 2017-05-31
Have you checked if those Atom CPUs are 64bit? I think they should be, almost all new CPUs are 64bit. In that case, I think the image you downloaded is correct, the standard server amd64 image should work.

I don't know what else to say, this is strange error. Can you try another usb stick? Or even a cd and usb cd-rom if you have one? Sometimes creating those bootable usb sticks on windows leads to unexpected behavior. If you have a usb cd-rom get any cdrw and try installing with a cd.

---

