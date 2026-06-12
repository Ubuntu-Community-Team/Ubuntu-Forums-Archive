---
title: "does any one know how to use dnspktflow?"
date: 2010-01-14
forum: Security
---

### Post by el_fiqs on 2010-01-14
i'm unable to install this features and does not know how to produce the output, please help

---

### Post by Ilalmi on 2010-01-16
```
sudo apt-get install dnssec-tools
``` should install it. 

Have a look at [http://manpages.ubuntu.com/manpages/karmic/man1/dnspktflow.1p.html](http://manpages.ubuntu.com/manpages/karmic/man1/dnspktflow.1p.html) to see, how to use it.

Hope that gets you any further.

---

### Post by el_fiqs on 2010-01-17
oh, thanks.. i've run the apt-get install dnssec-tools command and successfully install it. when i run command dnspktflow -o output.png file.tcpdump. output.png produce but nothing contain in the file. please help me..

---

### Post by Ilalmi on 2010-01-17
Do you get an error message?

Download the example file dns.cap from [http://wiki.wireshark.org/SampleCaptures?action=AttachFile&do=get&target=dns.cap](http://wiki.wireshark.org/SampleCaptures?action=AttachFile&do=get&target=dns.cap) and try ```
dnspktflow -o output.png dns.cap
``` using the downloaded file

---

### Post by cariboo on 2010-01-17
Are you running tcpdump and creating a file for dnspktflow to read?

Check out man tcpdump for more info.

---

### Post by el_fiqs on 2010-01-19
i didnt get any error msg. the output is produced like a small circle and have no picture in the files. did i not successfully install the software?

---

### Post by Ilalmi on 2010-01-20
Hmm, I think that if you hadn't installed the software successfully, the only output you would get would be an error.

[LIST=1]
[*]Did you download and use the dns.cap file for your try?
[*]Are you using tcpdump to create the file.tcpdump, like cariboo907 suggested?
[*]Could you post your output.png?
[/LIST]

---

### Post by el_fiqs on 2010-01-20
i av successfully can produce the output, i av recheck that i missing tshark before this. thanks guys for your support ;)

---

