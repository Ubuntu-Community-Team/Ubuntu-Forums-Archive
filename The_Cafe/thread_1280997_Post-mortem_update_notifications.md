---
title: "Post-mortem: update notifications"
date: 2009-10-02
forum: The Cafe
---

### Post by Arand on 2009-10-02
Now, when most of the dust has settled, and we've had our time to consider, reconsider, and settle. I though it would be interesting to look back on what must've been one of the more debated decisions for 9.04 Jaunty, the redesign of the update notifications behaviour:

> Ubuntu 9.04 introduces a change to the handling of package updates, launching update-manager directly instead of displaying a notification icon in the GNOME panel. Users will still be notified of security updates on a daily basis, but for updates that are not security-related, users will only be prompted once a week. 

Soo, in the aim of seeing whether the decision was the right one, now when we've been and seen it all, I though a poll would be intriguing.

- Arand

---

### Post by Tibuda on 2009-10-02
You can change it back in gconf-editor, uncheck /apps/update-notifier/auto_launch

---

### Post by Arand on 2009-10-02
> **danielrmt said:**
> You can change it back in gconf-editor, uncheck /apps/update-notifier/auto_launchYes, I'm assuming everyone knows that by know (it's in the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/904#Change%20in%20notifications%20of%20available%20updates") after all). 
I'm instead looking for the general opinion, since it seems this is a scheme that's sticking in karmic as well.
I wanted to know if the apparent silence is due to people being happy/indefferent/resigned towards it.
- Arand

---

### Post by kevCast on 2009-10-02
Good idea. An orange icon isn't enough for people who aren't knowledgeable about computers. They need it to launch and inform them automatically.

---

### Post by pt123 on 2009-10-02
They seem to not use it for useful things like : when a file operation is finished, or to update it's progress every minute.

---

### Post by Warpnow on 2009-10-02
I don't like it.

---

