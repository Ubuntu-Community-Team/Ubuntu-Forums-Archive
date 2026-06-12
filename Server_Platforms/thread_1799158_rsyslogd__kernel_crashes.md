---
title: "rsyslogd / kernel crashes"
date: 2011-07-07
forum: Server Platforms
---

### Post by Lord_ on 2011-07-07
Hi everyone,

I have an issue with server which has started to crash for the last couple of days. I believe that the crash is related to either CPU problems or rsyslogd, which appears at the start of the crash logs with a strange notices about its uid changing. (not sure why it would want to do this!)

For the record, its a vmware guest and 2 extra cores were added a couple of weeks back. Also on login it mentions that the nx settings are missing. This is something I can enable in vmware but have not encountered the need to before.

Your CPU appears to be lacking expected security protections.
Please check your BIOS settings, or for more information, run:
  /usr/bin/check-bios-nx --verbose


Below are two versions of the crash dump. One from yesterday, at which time I was running 10.04, and one from today since I did the upgrade to 10.10, hoping the newer kernel would resolve. It seems to be the same problem.


I have attached the relevant output from /var/log/messages

---

