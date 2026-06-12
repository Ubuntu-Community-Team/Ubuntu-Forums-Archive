---
title: "a feature i would like to have"
date: 2019-02-02
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2019-02-02
if anyone knows of a kernel module that can add this feature i would very much appreciate information about where to get it.  the feature is like the **[FONT=courier new]/dev/null[/FONT]** device which when read from, succeeds with an end-of-file condition, and when written to, succeeds and discards the data that was written.  my idea is a device i would call **[FONT=courier new]/dev/block[/FONT]**.  when read from or written to it would block the process unless the file descriptor had been set in non-blocking mode.  in non-blocking mode it would fail with errno set to EAGAIN or EWOULBLOCK to indicate that data for reading or space for writing is not currently available.  it would never have these available so program that wait for i/o correct would wait forever.  use cases would include being a quick way to test programs.  it would also be a perpetual input source for programs, scripts, or commands that could react in undesired ways when receiving some data or end-of-file.

---

