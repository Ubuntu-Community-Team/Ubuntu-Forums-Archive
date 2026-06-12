---
title: "Which packages recommended to use spice with kvm?"
date: 2014-08-31
forum: Virtualisation
---

### Post by Remten on 2014-08-31
Which package(s) should I install to be able to use spice, rather than vnc, with kvm?
This would be for, for example, a desktop Kubuntu 14.04 hosting another linux version in the VM.

---

### Post by KillerKelvUK on 2014-08-31
Don't  think you've that many different choices but I have installed the following...

```

dpkg -l | grep spice
ii  libspice-client-glib-2.0-8:amd64                      0.22-0nocelt2                                       amd64        GObject for communicating with Spice servers (runtime library)
ii  libspice-client-gtk-2.0-4:amd64                       0.22-0nocelt2                                       amd64        GTK2 widget for SPICE clients (runtime library)
ii  libspice-client-gtk-3.0-4:amd64                       0.22-0nocelt2                                       amd64        GTK3 widget for SPICE clients (runtime library)
ii  libspice-server1:amd64                                0.12.4-0nocelt2                                     amd64        Implements the server side of the SPICE protocol
ii  python-spice-client-gtk                               0.22-0nocelt2                                       amd64        GTK2 widget for SPICE clients (Python binding)
ii  spice-client                                          0.12.4-0nocelt2                                     amd64        Implements the client side of the SPICE protocol
ii  spice-client-glib-usb-acl-helper                      0.22-0nocelt2                                       amd64        Spice client glib usb acl helper
ii  spice-vdagent                                         0.14.0-1ubuntu1                                     amd64        Spice agent for Linux



```

---

### Post by Remten on 2014-09-02
thanks for the reply

---

