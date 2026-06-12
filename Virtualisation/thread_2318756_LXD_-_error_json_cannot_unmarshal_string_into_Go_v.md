---
title: "LXD - error: json: cannot unmarshal string into Go value of type int64"
date: 2016-03-29
forum: Virtualisation
---

### Post by nick246 on 2016-03-29
Have successfully installed LXD on Ubuntu Server 15.10. However, tried running "lxc image list images:" without success - on two different clean server installations.

The error this command returns is:
"error: json: cannot unmarshal string into Go value of type int64".

The getting started documentation is simple and clear - there isn't much to get wrong.

[LIST=1|INDENT=1]
[*]logged into server with non-root user.
[*]ran "[FONT=lucida console]sudo apt-get update[/FONT]"
[*]ran "[FONT=lucida console]sudo apt-get upgrade[/FONT]"
[*]ran "[FONT=lucida console]sudo apt-get install lxd[/FONT]"
*successful LXD installation.*
[*]login/logout to refresh group membership.
[*]ran "[FONT=lucida console]lxc remote add images images.linuxcontainers.org[/FONT]" (no sudo from this point onward).
[I]certificate was created successfully and was advised:
[/I]"[FONT=lucida console]If this is your first run, you will need to import images using the 'lxd-images' script. 
For example: 'lxd-images import ubuntu --alias ubuntu'[/FONT]."
*- the advice in this return differed from the [how-to]("https://insights.ubuntu.com/2015/04/28/getting-started-with-lxd-the-container-lightervisor/") and I took the return as authoritative, especially as my previous attempt following the how-to caused the error listed, as happened again in this procedure.*
[*]ran "[FONT=lucida console]lxd-images import ubuntu --alias ubuntu[/FONT]"
[I]successful download and validation of the GPG key for "http://cloud-images.ubuntu.com"
[/I]*successful connection and start of image download...*
[*]at this point I cancelled the download (ctrl-c), as I wanted to move on to see if either ubuntu core or coreos was available in the library.
[*]ran "[FONT=lucida console]lxc image list images:[/FONT]" [I]which resulted in the same error as on previous server: 
[/I]"[FONT=lucida console]error: json: cannot unmarshal string into Go value of type int64[/FONT]".
[/LIST]

It is strange that the image library cannot be viewed in a browser so that the right image can be found and its name typed directly into the CLI.

The inevitable conclusion is that either the how-to is missing something, or the technology isn't ready for the method described in the how-to. Has anyone encountered this problem? If you haven't, and you were immediately able to list available images, please feel free to share!

A fix for this issue has been to run the following sequence, which did not work for me:

[LIST=1]
[*]run "[FONT=lucida console]sudo apt-get install lxc[/FONT]", *returned 'lxc is already the newest version.'*
[*]run "[FONT=lucida console]sudo apt-get dist-upgrade[/FONT]", *performed new installations and upgrades of linux-headers, linux-image, linux-signed-image files only.*
[/LIST]
Someone provided me with image names and aliases, so using [FONT=lucida console]"lxd-images import ubuntu xenial --alias[/FONT][FONT=lucida console] ubuntu/xenial/amd64[/FONT][FONT=lucida console]"[FONT=verdana] I was able to download an image and create the first container. Everything else seems to be working[/FONT].[/FONT]

Thanks everyone.

Cheers,
nick

---

### Post by nick246 on 2016-04-06
OK, a reinstallation and more careful following of the recommended procedure resulted in two new server installations (15.10) without the above error and full LXD functionality. I attribute this success to:
1. installing with 'sudo';
2. using lxc commands *without '*sudo'.

In the above scenario I *did* use 'sudo' in the first instance to run 'lxc remote add images images.linuxcontainers.org'. However, I believed that I had corrected the permissions and ownership on the installed files and directory, and negated a possible cause of the error. Clearly, an incorrect presumption - although, I cannot also presume that the use of 'sudo' to add linuxcontainers.org did in fact cause the error. Yeah, dumb newbie mistake. Can I just delete my pointless initial post?

So, as a possible cause for the json error I recommend users attempt to recall if they used 'sudo' to run any lxc commands.

---

