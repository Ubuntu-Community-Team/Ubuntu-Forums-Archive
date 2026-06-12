---
title: "updating dns"
date: 2011-06-02
forum: Server Platforms
---

### Post by tapi0n on 2011-06-02
I'm writing a bash script to add new domains.

The script makes a new zone file, adds the zone file to named.conf and adds a NS record to my db.me.

The script itself runs like it's supposed to (in a local test environement) but I got a question about updating the dns serial.

I'm able to get the current serial by running

```
serienr=`cat db.me | grep 'serial' | grep -E '[0-9]{1,}' -o`

```to update the serial I use the following command

```
nieuw=$(($serienr+1))

```Now my question is the this, how do I get the new serial (*nieuw) *into db.me? Does Ubuntu provide some sort of way to do this automatically?

Cheers

Edit: found out about [sed]("http://www.grymoire.com/Unix/Sed.html") which does just what I needed.

---

