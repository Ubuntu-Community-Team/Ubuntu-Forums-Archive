---
title: "How do I expand a volume when my array grows?"
date: 2011-03-07
forum: Server Platforms
---

### Post by OneSeventeen on 2011-03-07
I use an iSCSI SAN to host all my data and am creating a separate volume for MySQL databases.  If I need to grow the volume, it is a simple text field in my SAN management interface.

Once I grow that volume, is it possible for Linux to rescan the drives and then expand to use up the rest of the newly available storage space?

(In Windows this is done by going into disk manager, right clicking and choosing something like "rescan drives" then when the new space shows up I just either right-click and choose expand or use the command line to expand the volume... usually takes about 1 minute and can be done while users are accessing data on the partition)

If this isn't possible/reliable, then I guess I can always create a new volume, migrate the data, then unmount the old drive and mount the new drive where the old one was... but that seems pretty lame for a production server.

---

