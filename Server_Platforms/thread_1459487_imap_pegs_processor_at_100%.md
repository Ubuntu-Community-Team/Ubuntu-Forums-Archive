---
title: "imap pegs processor at 100%"
date: 2010-04-21
forum: Server Platforms
---

### Post by digitolx on 2010-04-21
Hello, first post here,, so hi all.. 

I've been having an issue where imap will peg the processor and slowly eat up all processing capability. It will even eat up the separate cores if left running too long. The only solution is to restart cyrus 2.2 and if that doesn't work the process would need killed.. Then cyrus restarted.

I ran an strace on the process and recieved the following..

poll([{fd=14, events=POLLIN|POLLPRI|POLLERR|POLLHUP}], 1, -1) = 1 ([{fd=14, revents=POLLIN|POLLERR|POLLHUP}])
poll([{fd=14, events=POLLIN|POLLPRI|POLLERR|POLLHUP}], 1, -1) = 1 ([{fd=14, revents=POLLIN|POLLERR|POLLHUP}])
poll([{fd=14, events=POLLIN|POLLPRI|POLLERR|POLLHUP}], 1, -1) = 1 ([{fd=14, revents=POLLIN|POLLERR|POLLHUP}])

This just repeats itself.. Does anyone have an idea on where/how to troubleshoot this farther?

thanks in advance

---

