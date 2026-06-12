---
title: "Possible hack?"
date: 2008-10-23
forum: Server Platforms
---

### Post by quikone8 on 2008-10-23
Can someone look at the following tests and first of all tell me if my system has been hacked, and if so how the heck do I fix it?  Also, so far
        


ron@tolmarket:~$ pstree -p
init(1)&#9472;&#9516;&#9472;NetworkManager(6052)&#9472;&#9472;&#9472;{NetworkManager}(6841)
        &#9500;&#9472;NetworkManagerD(6066)
        &#9500;&#9472;acpid(5831)
        &#9500;&#9472;atd(7034)
        &#9500;&#9472;avahi-daemon(6131)&#9472;&#9472;&#9472;avahi-daemon(6132)
        &#9500;&#9472;bonobo-activati(7286)&#9472;&#9472;&#9472;{bonobo-activati}(7291)
        &#9500;&#9472;citserver(6979)&#9472;&#9472;&#9472;citserver(6980)&#9472;&#9516;&#9472;{citserver}(7076)
        &#9474;                                   &#9500;&#9472;{citserver}(7077)
        &#9474;                                   &#9500;&#9472;{citserver}(7078)
        &#9474;                                   &#9500;&#9472;{citserver}(7081)
        &#9474;                                   &#9500;&#9472;{citserver}(7082)
        &#9474;                                   &#9500;&#9472;{citserver}(7083)
        &#9474;                                   &#9500;&#9472;{citserver}(7084)
        &#9474;                                   &#9492;&#9472;{citserver}(7085)
        &#9500;&#9472;console-kit-dae(6740)&#9472;&#9516;&#9472;{console-kit-dae}(6741)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6742)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6743)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6744)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6745)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6746)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6748)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6749)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6750)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6751)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6752)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6753)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6754)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6755)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6756)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6757)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6758)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6759)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6760)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6761)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6762)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6763)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6764)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6765)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6766)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6767)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6768)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6769)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6770)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6771)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6772)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6773)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6774)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6775)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6776)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6777)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6778)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6779)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6780)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6781)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6782)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6783)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6784)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6785)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6786)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6787)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6788)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6789)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6790)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6791)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6792)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6793)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6794)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6795)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6796)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6797)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6798)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6799)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6800)
        &#9474;                       &#9500;&#9472;{console-kit-dae}(6801)
        &#9474;                       &#9492;&#9472;{console-kit-dae}(6951)

---

### Post by plasmafusion on 2008-10-23
so you've got citadel, console-kit-daemon and other normal stuff running...why do you think you've been hacked in some way? all other processes look stock to me.

---

