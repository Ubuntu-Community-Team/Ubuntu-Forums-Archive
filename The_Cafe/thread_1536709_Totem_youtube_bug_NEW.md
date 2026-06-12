---
title: "Totem youtube bug NEW"
date: 2010-07-22
forum: The Cafe
---

### Post by limestone on 2010-07-22
Ok, I can't get the ubuntu bug report to work so I just want to confirm this. Again after the latest updates in Ubuntu totem says "Could not open location; you might not have permission to open the file." when trying to view a youtube film. It also gives me this output.

> Message: Error: "http://www.youtube.com/get_video?video_id=SPGWRS9B5_0&t=vjVQa1PpcFP0-3Dzqwv9NRtwrsMorN5SczRJqWjbRnQ%3D&fmt=18": Not Found
gstsouphttpsrc.c(1096): gst_soup_http_src_parse_status (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstSoupHTTPSrc:source:
404 Not Found

---

### Post by FuturePilot on 2010-07-22
Confirmed. However it probably has nothing to do with updates. Youtube probably changed something on their end that broke it.

---

### Post by urukrama on 2010-07-22
> **FuturePilot said:**
> Confirmed. However it probably has nothing to do with updates. Youtube probably changed something on their end that broke it.

You are probably right. Youtube-dl no longer works either.

---

### Post by limestone on 2010-07-22
> **FuturePilot said:**
> Confirmed. However it probably has nothing to do with updates. Youtube probably changed something on their end that broke it.

True.. due to the link totem gives out leads to an empty page...

---

### Post by nilarimogard on 2010-07-23
Yes, it's 100% because of youtube. As for youtube-dl, you can get a working version from [here]("http://www.webupd8.org/2010/07/update-youtube-dl-to-get-it-working.html").

---

