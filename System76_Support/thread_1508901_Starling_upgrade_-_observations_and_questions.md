---
title: "Starling upgrade - observations and questions"
date: 2010-06-13
forum: System76 Support
---

### Post by jangat on 2010-06-13
I have had a starling since the beginning of the year. Yesterday I upgraded to 10.4 and although things seem to be OK, I have questions about a couple of things.


[LIST]
[*]I was asked during the install if I wanted to accept changes to the file "/etc/modprobe.d/alsa-base.conf".  I did accept the changes.
[*]I was asked if I wanted to keep the current grub-pc configuration or accept modifications. I declined the modifications.
[/LIST]
In both cases I was guessing since I really had no idea what the impact of my choices would be. Could someone please tell me if I should have done otherwise.

When I went to install the system76 drivers per the instructions on the system76 upgrade instructions, I found the following in my Software Sources application, under the 'Other Software' tab:

**disabled on upgrade to lucid** ([http://planet76.com/repositories/./)]("http://planet76.com/repositories/./")

This is not what the screenshot in the system76 instructions shows. Is there any significance here? I ended up installing the drivers manually.

Except for these hopefully insignificant details (although they are bothersome to a casual user), the upgrade seems to have gone well. All my other "stuff" appears to have survived.

Thanks for any comments.

Jan G.

---

### Post by isantop on 2010-06-14
Good to hear of a successful upgrade! 

The "Disabled on Upgrade to Lucid" error seems pretty common. Installing the drivers manually almost always fixes the problem. You shouldn't see any problems.

During pretty much any upgrade (to new Ubuntu versions or otherwise) it is usually a good idea to accept modifications to config files. Usually, these are overwriting custom user changes, but they replace the files in question with versions directly from the developer. They are usually fully compatible with any changes the developer made to the program, so you should use them to ensure compatibility.

However, if you have seen no problems with your GRUB configuration (i.e. your system boots.) then you should be okay.

---

