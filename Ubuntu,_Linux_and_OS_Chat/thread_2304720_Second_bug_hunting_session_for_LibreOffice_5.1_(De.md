---
title: "Second bug hunting session for LibreOffice 5.1 (Dec 4 to Dec 6, 2015)"
date: 2015-11-29
forum: Ubuntu, Linux and OS Chat
---

### Post by Buovjaga on 2015-11-29
Welcome to the session: [https://blog.documentfoundation.org/blog/2015/11/17/second-bug-hunting-session-for-libreoffice-5-1/](https://blog.documentfoundation.org/blog/2015/11/17/second-bug-hunting-session-for-libreoffice-5-1/)

In other news, the LibreOffice quality assurance team is looking for new members! No real upper limit, 100 new members welcome ;)

I am available for mentoring. It is pretty [easy to get started]("https://wiki.documentfoundation.org/QA/Triage_For_Beginners"), but there are lots of little things to learn along the way.
Learning [advanced triaging]("https://www.youtube.com/watch?v=WLmEfvjVN7s") will give you superpowers and your work will make bug fixing much faster for developers.

Join us on IRC, [#libreoffice-qa @ Freenode]("https://kiwiirc.com/client/irc.freenode.net/libreoffice-qa").

---

### Post by brianewalsh2 on 2015-11-30
Its funny that this was posted yesterday, as I have been experiencing a lot of graphics issues with Writer in Gnome on 15.10. Lines of text spliced together, incorrect fonts, 'document jumping' (suddenly I'll go from the top of the document to the bottom), suddenly sections of the document are bolded, ect.. The only issue is that I dont see any of this what so ever if I pop over into Mate and look at the same doc. So Im not sure where the fault lies.

---

### Post by Buovjaga on 2015-11-30
brianewalsh2: do you see the issues under Gnome, even if you launch LibreOffice from the command line with:
SAL_USE_VCLPLUGIN=gtk soffice

I'm asking, because you might have the gtk3 plugin installed and LibreOffice is using it.. it is still an experimental feature though, so should not be enabled by default.

The command for launching with gtk3 is:
SAL_USE_VCLPLUGIN=gtk3 soffice

---

### Post by brianewalsh2 on 2015-11-30
very nice! thanks for your rapid reply! that was it exactly. wow I wish I had known you could launch it without the plugin feature days ago. I open the same doc with and without the gtk3 plugin and from my brief observations it was the cause of my trouble.

---

