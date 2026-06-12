---
title: "Zenity on the server side"
date: 2012-06-28
forum: Ubuntu Application Development
---

### Post by Latinpower on 2012-06-28
Is there a way to execute shell scripts with Zenity commands on a non-graphical server?.

I need users to connect by SSH to the server, and I'd like them to see the graphic interface I've made with Zenity.

I know it is impossible to see the GUI on the server side, but can I only show it on the client side?

Thanks

------
Solved!

I just needed to use Session Forwarding

Like this : 

ssh -X [email]username@desktopmachine.domain.com[/email]

---

