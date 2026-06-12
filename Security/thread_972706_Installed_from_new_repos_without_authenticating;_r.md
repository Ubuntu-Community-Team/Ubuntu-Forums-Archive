---
title: "Installed from new repos without authenticating; risky?"
date: 2008-11-06
forum: Security
---

### Post by conphuzed on 2008-11-06
i installed xbmc by adding the xbmc repos but there were no keys anywhere to authenticate with so i just installed without authenticating. later on some updates popped up and it said again that they were not authenticated (i couldn't really tell if the updates were related to xbmc or not). i installed those too.

the xbmc website is a trusted source i think but is this risky in some way? can a malicious update pop up? no idea how this works..

---

### Post by EXCiD3 on 2008-11-06
what it means is that you did not have a GPG key to verify the identity of the server you are downloading from. XBMC is a trusted source and as long as you are sure its the correct URL then you are fine. this is an added security feature to ensure the person/server your are communicate with is who they truly say they are. sometimes they dont give you a key to verify them with and you will just have to use it unauthenticated.

---

### Post by conphuzed on 2008-11-07
okay thanks!

---

