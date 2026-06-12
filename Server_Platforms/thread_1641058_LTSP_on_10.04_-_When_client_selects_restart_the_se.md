---
title: "LTSP on 10.04 - When client selects restart the server restarts"
date: 2010-12-08
forum: Server Platforms
---

### Post by mikeatx on 2010-12-08
I just setup an LTSP server at our office and doing some testing.

I found by default each user has the power icon in the upper right of the screen with Lock, logout, restart and shutdown options. The restart and shutdown options actually restart the server.

I'd like to do two things; simply remove the shutdown/restart option and make sure normal users don't have permissions to reboot the server. 

I'm also a bit confused by how LTSP behaves. I initially chrooted to /opt/ltsp/amd64 and installed software I wanted but found when I PXE booted a laptop to that environment nothing I installed was there, nor was the laptop actually chrooted into /opt/ltsp/amd64. I found installing applications directly on the server works fine but that wasn't my understanding of how this works. Is /opt/ltsp/amd64 only used for building to tftp image and otherwise not used?

This is a default install from the Ubuntu 10.04 x86_64 alternative CD using the LTSP server option.

---

