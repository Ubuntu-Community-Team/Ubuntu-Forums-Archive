---
title: "Folders sync for a while, then stop"
date: 2012-01-09
forum: Ubuntu One (CLOSED)
---

### Post by leupi on 2012-01-09
I have a handful of folders on an Ubuntu server that I am syncing with Ubuntu One and they sync for a while then stop and I get the message:
> The folder cannot be synchronized because it contains one or mored folders that are already synchronized
I ran the command u1sdtool --list-folders and got this:
```
  id=41a71bc8-f053-49fe-ba18-146ac6af1b55 subscribed=False path=/home/tparks/server/gnucash
  id=e680a2df-f0af-4723-b973-dd8a1d496579 subscribed=False path=/home/tparks/server/gramps
  id=1d69bcf7-c1b8-4d07-89a0-ccb1b5b1c14b subscribed=False path=/home/tparks/server/Linux
  id=825b6ca0-780b-42a6-b605-107fe6dc637f subscribed=False path=/home/tparks/server/personal files
  id=abff7182-8523-4a38-bfb4-6e00a7603f62 subscribed=True path=/home/tparks/Pictures
  id=dcd3c81b-926f-4a46-9435-dd2c07dc42b7 subscribed=True path=/home/tparks/Pictures - LG-P509
```
My '/home/tparks/Pictures - LG-P509' and '/home/tparks/Pictures' are syncing fine, it is just the folders that are on the server that are no longer syncing. They synced fine for a while and I just noticed today that they have stopped and this is not the first time that this has happened. If I remove them from Ubuntu One and then resync them from my laptop they will start to synce again but that is really a PITA. Any thoughts?

---

