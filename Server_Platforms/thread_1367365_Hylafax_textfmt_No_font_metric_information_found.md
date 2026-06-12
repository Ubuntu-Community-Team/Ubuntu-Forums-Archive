---
title: "Hylafax: textfmt: No font metric information found"
date: 2009-12-29
forum: Server Platforms
---

### Post by falstaff on 2009-12-29
Hi,

I installed hylafax on my Ubuntu 9.10 64-Bit Server. When I try to send a fax I get this:
```

# sendfax -n -d 1234567 /etc/issue.net 
textfmt: No font metric information found for "Courier-Bold".
Usage: textfmt [-1] [-2] [-B] [-c] [-D] [-f fontname] [-F fontdir(s)] [-m N] [-o #] [-p #] [-r] [-U] [-Ml=#,r=#,t=#,b=#] [-V #] files... >out.ps
Default options: -f Courier -1 -p 11bp -o 0
Error converting document; command was "textfmt -B -f Courier-Bold	-Ml=0.4in -p 11 -s default >'/tmp//sndfaxUSNM62' <'/etc/issue.net'"

```

I allready searched with google, but found no solution. Acctually the problem seems to be very old, but I installed a new Ubuntu from scratch and get this...

Any idea?

Thanks
bye
falstaff

---

### Post by falstaff on 2009-12-29
I solved it by testing not with an ASCII file, but a PNG instead:

```

$ sendfax -n -d 0764203538 /usr/share/pixmaps/debian-logo.png

```

In the file /etc/hylafax/typerules is the command with wich textfmt is called. I removed the font there (and the Parameter -f). I then get another message, but no fax in the queue... Therefor I switched to the PNG solution...

Bye
falstaff

---

### Post by chrisrd on 2010-03-04
> **falstaff said:**
> I solved it by testing not with an ASCII file, but a PNG instead:


Well... that's one permutation of "solved".  :-)

On the other hand, if you want to actually fix the problem so you can fax text files, you need to find the directories containing 'Fontmap' or 'Fontmap.GS' file[s] and put these directories (separated by colons if there are more than one directory) into the 'FontMap' entry in /etc/hylafax/hyla.conf

On my Ubuntu 9.10 it's:

FontMap: /var/lib/defoma/gs.d/dirs/fonts

A more generic solution would be:

fm=`locate Fontmap | perl -ne 'chomp; if (s!/Fontmap(?:\.GS)?$!!) { $d{$_}=1; } END { print join(":", keys %d), "\n" } '`
if [ "$fm" ]
then
  perl -pi -e's!^(FontMap:\s*).*!$1'${fm}'!' /etc/hylafax/hyla.conf
else
  echo "Sorry, can't find any Fontmap files"
fi

---

