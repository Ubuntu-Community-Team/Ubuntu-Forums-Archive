---
title: "News Reader (nzb, good handling of LARGE groups, more...)"
date: 2009-09-15
forum: Server Platforms
---

### Post by Pro_D on 2009-09-15
Something of a fishing topic...  I have searched around some already but haven't found a good match yet.  There are SO many options too.

I am after a news (nntp) reader.  At minimum it needs:
-good support for LARGE groups (the current program we use chokes on 40 days worth of headers - newsleecher)
-easily searchable
-be able to log into the news server.  Several of the readers I looked at had no way to login (ie meant to work with an open nntp server).
-keep a local cache - again several didn't keep a local cache.
-save a set of article IDs to NZB file.
-Does NOT need to be able to post or read articles!  Reading of non-binary articles would be a big plus though.

Additional items that would be great:
-Allow multiple groups to be 'open' at the same time, preferably not all groups at the same time though.
-web interface - even if multipart (ie needs separate reader and web interface).
-multi-user single database.
-ability to handle encrypted server connection (very low importance).

From a usability standpoint coming from newsleecher.  Yes I know of it's 'super search' ability as well as searching on other websites however searching is perhaps 50% of usage at most and most sites/systems I have seen are too broad in focus.

While it would be neat if there was something like this already out there, I can probably contribute to a project that has a lot of this or has similar goals but is incomplete so don't hesitate to throw something like that up :) .

The platform I have right now:
Ubuntu-server 9.04 (was 8.04 but had series of major hardware failures).
Ubuntu-desktop is on top w/vnc (lan access only) so a standard interface becomes acceptable.
Apache for web-hosting (again, lan only)

Another alternative would be to have the our server download headers from the nntp server on the internet but ONLY from a *FEW* groups.  Then we would have to find programs that allow for live access to that w/nzb support.  I have done very little research on this though.  What I did find made this seem infeasible.

---

### Post by windependence on 2009-09-15
What's wrong with Thunderbird?

-Tim

---

### Post by Pro_D on 2009-09-15
I never said anything was wrong with it, in fact if I figured out how to have the server system cache just specific groups and then act as an NNTP server itself, this would be among the first readers I would investigate for users to make nzb files from.

This is a fishing topic though and I am hoping someone comes along with a bit more knowledge than I have on the topic and can point me to a few potentially promising projects (not necessarily from a single person).  A strait up news reader is fine but I am hoping to come across something that hits on some of the optional elements in that list.

---

