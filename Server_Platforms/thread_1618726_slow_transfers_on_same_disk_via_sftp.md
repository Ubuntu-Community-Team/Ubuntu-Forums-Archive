---
title: "slow transfers on same disk via sftp"
date: 2010-11-11
forum: Server Platforms
---

### Post by senor_smile on 2010-11-11
I have a remotely hosted server that users are accessing via chrooted sftp.  There is a temp folder for initial uploads that will stage the files.  After a while those files will then be organized into other folders.  The problem is that when transferring the files into other folders on the same drive(say 100 MB - 5 GB at a time), the transfers seem to take forever.  If I do it via cp -R it is almost instantaneous.  What is a way I can provide the users who do not have ssh shell access to be able to transfer files without it taking forever?

---

