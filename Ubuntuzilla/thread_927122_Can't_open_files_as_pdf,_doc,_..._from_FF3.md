---
title: "Can't open files as pdf, doc, ... from FF3"
date: 2008-09-22
forum: Ubuntuzilla
---

### Post by teknoman on 2008-09-22
Hi all.

I've installed FF3 via ubuntuzilla on a Kubuntu Gutsy Gibbon.
In general it works very well.

The only issue is the following:
If I try to open directly an file such a pdf or doc or odt or whatever you want an error window appear with a something like that: 
(I will translate it from catalan, sorry for possible mistakes):

"Can't open /tmp/filename because associated helper application doesn't exist. Change association in your preferences"

The curious fact is that in previous window (the one that let you choose if you want to download the file or to open it directly) it recognizes the file type and proposes the right application to use (for example, Adobe Reader 8, OpenOffice Writer, ...).

If you don't choose this default application name and choose "Other", navigate and try the executable file (for example /usr/bin/acroread or /usr/bin/soffice) the it works perfectly.

Well. That's solves the problem for me, but I can't make users in my school network to do that as they could kill me.

All these files types were correctly opened in FF2.

How can I make FF3 (installed via ubuntuzilla) to recognize properly all these file types?

Thank you in advance.

---

### Post by nanotube on 2008-09-23
Hi,

look here: 
[http://kb.mozillazine.org/The_associated_helper_application_does_not_exist](http://kb.mozillazine.org/The_associated_helper_application_does_not_exist)

in particular, look at the section at the bottom about mimetypes.rdf. looking at that file, you should be able to diagnose exactly what's going on... (that file should contain the currently-set full paths for the applications that are associated with the filetypes. if they are not in /usr/bin, well, then, there's your problem.)

so, to fix this, two alternatives: change your chosen apps to point to the correct paths as you encounter the "open with" dialog, or two, delete (well, back it up) the mimeTypes.rdf file in your profile, and firefox should automatically regenerate it.

---

### Post by rubioxtu on 2008-10-03
Looking for a solution I found [[COLOR="Blue"]this[/COLOR]]("http://devgon.wordpress.com/2008/05/13/hacer-que-firefox-3-beta-5-abra-archivos-descargados-como-estan-asociados-en-kde/") and it works.

Just make a script:

$ kdesu kate /usr/bin/openwith

Paste this inside:

#!/bin/bash
kfmclient exec $1

Make it exe:

$ sudo chmod +x /usr/bin/openwith

When firefox asks just select the script:

/usr/bin/openwith

Firefox will open every file with the Kde associated application.

Sorry for my English

---

