---
title: "read if you have update repository problems in Dapper 6.06"
date: 2006-09-23
forum: Repositories &amp; Backports
---

### Post by shailbond on 2006-09-23
If your package manager fails to fetch data from repositories do the following actions to fix this. This is probably a bug in Package manager.

        On terminal type sudo gedit /etc/apt/sources.list to open and edit the file. open another terminal or system>administration>network tools. inthe open file wherever you find a web address e.g archive.ubuntu.com , security.ubuntu.com replace it with ipv4 address. So your entry will look like now
deb [http://123.123.123.123/ubuntu](http://123.123.123.123/ubuntu) ...... .
instead of

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) ....

. where 123.123.123.123 is the address u obtain when u ping respective web addresses.

Same way u can connect ur GAIM or evolution by giving ipv4 addresses in place of web addresses.
However firefox is all right . You dont need anything for that.

Hope this works. Happy computing
Edit/Delete Message

---

