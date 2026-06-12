---
title: "scp publickey fails but sftp succeeds"
date: 2012-11-28
forum: Server Platforms
---

### Post by dpouliot on 2012-11-28
Sorry if this is the wrong place for this question but I'm not sure the right place to go.

I just upgraded my Web server from Ubuntu 10.04 to 12.04. Everything is going great except for one small issue:

When I try scp  I get Permission denied (publickey).

This surprises me. I have updated my known_hosts file and sftp and ssh are both successful.

 Hopefully this is a simple issue. Any help is greatly appreciated!

---

### Post by SeijiSensei on 2012-11-28
The user account you're using probably doesn't have write permissions to the remote location.

---

### Post by dpouliot on 2012-11-29
If found I needed to tweak my ssh settings to allow this user to log in. thanks SeijiSensei!

---

