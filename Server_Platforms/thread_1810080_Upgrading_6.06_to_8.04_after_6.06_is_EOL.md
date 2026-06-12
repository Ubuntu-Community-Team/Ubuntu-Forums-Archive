---
title: "Upgrading 6.06 to 8.04 after 6.06 is EOL"
date: 2011-07-22
forum: Server Platforms
---

### Post by hobbestec on 2011-07-22
I am trying to run do-release-upgrade on my 6.06 server to upgrade it to 8.04, however I am getting an error that says: Getting upgrade prerequisites failed.  

I've already changed my sources list to use the old-releases.ubuntu.com url for dapper, dapper-updates, dapper-security, and dapper-backports.  Then I ran apt-get update and upgrade with the most recent software.  Then ran do-release-upgrade and got that failure message.

The upgrade script made a file for prerequists-sources.dapper.list that has the old-releases.ubuntu.com url in it, but also has an entry for archive.ubuntu.com dapper-backports which isn't available anymore.  Is this a bug in the upgrader?

Is there some other way I need to be upgrading now that 6.06 is in the end of life?

---

