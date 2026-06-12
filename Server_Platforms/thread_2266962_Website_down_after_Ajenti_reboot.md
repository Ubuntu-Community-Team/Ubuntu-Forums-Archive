---
title: "Website down after Ajenti reboot"
date: 2015-02-26
forum: Server Platforms
---

### Post by noelllll on 2015-02-26
First I would like you to know that this problem is for a website that I took over ~6 months ago, so I didn't set it up and I'm not 100% familiar with Ajenti and what it can do. Also, I've tried creating a bug on Ajenti's website but it doesn't look like it'll be getting any attention any time soon, so this is why I ask here !

So, I just (about 1 1/2 hours ago) rebooted the server on the Ajenti Dashboard, using the "AC Power" Reboot button. At that point I was logged in to SSH for I got a message saying "The system is going down for reboot NOW!", and the Ajenti page became grayed out and says "Reconnecting" with the spinning arrow (still spinning, not frozen).

Like I mentioned it's been like this for about an hour now. When I try to SSH in now I get the error saying "Connection refused". When I go to the website in a browser I get "this page is not available".

I'm really starting to get worried because I really don't think it should be taking this long.. Please let me know what I can do to get this website back up and running. If you need any other information please let me know.

Thanks !

---

### Post by volkswagner on 2015-02-26
Where is the server hosted? You may need physical access or perhaps they have an IP KVM you can connect with.

Is it a physical server or virtual server?

You may have  just learned a hard lesson. Servers often have lengthy uptimes. A lot can change during this time.
Any update or file system change along the way could be the cause of the unresponsive server. It could be as simple
as firewall rules not properly configured.

---

