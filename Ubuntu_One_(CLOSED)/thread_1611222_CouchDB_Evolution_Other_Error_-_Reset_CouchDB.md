---
title: "CouchDB Evolution Other Error - Reset CouchDB"
date: 2010-11-01
forum: Ubuntu One (CLOSED)
---

### Post by ds_shellback on 2010-11-01
Since upgrading to Maverick I've experienced problems with UbuntuOne contact sync. There's been three blank lines at the start of the UbuntuOne list which I couldn't delete and attempts to delete or alter these or other contacts on UbuntuOne resulted in "Other Error"!

I followed the wiki guide to reset CouchDB contacts completely - this has allowed me to start afresh and copy the contacts back to UbuntuOne.

[https://wiki.ubuntu.com/UbuntuOne/ResetCouch]("https://wiki.ubuntu.com/UbuntuOne/ResetCouch")

A few things to note:-

To get to the CouchDB web interface I needed to use the following command in a terminal (remember to replace USERNAME with your user name!) and then bookmark the page.

```
xdg-open file:///home/YOURUSERNAME/.local/share/desktop-couch/couchdb.html
```

Select the contacts database and then delete and confirm from the CouchDB web interface.

I didn’t bother with the backup step since I already had the data locally.

Download the python script "ubuntuone-couchdb-query" from the wiki link and reset the UbuntuOne contacts database with the folowing command in a terminal:-

```
python ubuntuone-couchdb-query --http-method=DELETE contacts
```

I then had to reboot the computer to get evolution to forget the cached CouchDB data - perhaps someone can suggest a way to purge this without rebooting?

After this the UbuntuOne list in Evolution is completely reset.

I then uploaded fresh contacts to UbuntuOne by selecting "Copy all contacts" and selecting UbyntuOne from within Evolution.

Takes some time for the new contacts to appear in the UbuntuOne web interface.

---

