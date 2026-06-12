---
title: "Migrating data from HFS+ to Ext4"
date: 2017-04-03
forum: Server Platforms
---

### Post by mmatz on 2017-04-03
We are in the process of transitioning from a Mac OS X file server to an Ubuntu file server.  The volume on Mac OS X that needs to be copied to the Ubuntu server is 75GB.  The Ubuntu server has a 200GB volume for all the data.  The method of copy we chose is scp.  The copy is failing because the Ubuntu server is running out of free space.  How is this possible when the Ubuntu server volume is more than twice as large as the Mac OS X volume?
Thanks!
Mike

---

### Post by darkod on 2017-04-04
Strange indeed... I assume you are sure there are no hidden files, etc, and that the data size is really 75GB?

For the data that has copied before it stopped, can you compare if the size on hfs and ext4 is the same?

There might be small differences in used space because of chunk/sector size differences, but the data can't grow 3x...

---

