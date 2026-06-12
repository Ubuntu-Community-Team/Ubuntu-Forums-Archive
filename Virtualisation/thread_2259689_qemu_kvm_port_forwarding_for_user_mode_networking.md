---
title: "qemu kvm port forwarding for user mode networking"
date: 2015-01-06
forum: Virtualisation
---

### Post by redrumrogue on 2015-01-06
Hi folks,

I've created a new qemu-kvm guest using virt-manager in ubuntu 14.04.  This has been done in a qemu://session instance so the guest is using user mode networking (forgive me if my terminology isn't quite right, i'm still learning!).  I want to forward a port from the host to the guest.  I've done some reading online and found this solution - [http://snippets.webaware.com.au/howto/running-qemu-with-port-redirection-through-libvirt/](http://snippets.webaware.com.au/howto/running-qemu-with-port-redirection-through-libvirt/) - which seems to work fine.  However, I've been reading through the qemu man page and found this relating to the -net qemu command line argument ...
[HTML]
hostfwd=[tcp|udp]:[hostaddr]:hostport-[guestaddr]:guestport
               Redirect incoming TCP or UDP connections to the host port hostport to the guest IP address guestaddr on guest port guestport. If guestaddr is not
               specified, its value is x.x.x.15 (default first address given by the built-in DHCP server). By specifying hostaddr, the rule can be bound to a specific
               host interface. If no connection type is set, TCP is used. This option can be given multiple times.

               For example, to redirect host X11 connection from screen 1 to guest screen 0, use the following:

                       # on the host
                       qemu-system-i386 -net user,hostfwd=tcp:127.0.0.1:6001-:6000 [...]
                       # this host xterm should open in the guest X11 server
                       xterm -display :1

               To redirect telnet connections from host port 5555 to telnet port on the guest, use the following:

                       # on the host
                       qemu-system-i386 -net user,hostfwd=tcp::5555-:23 [...]
                       telnet localhost 5555

               Then when you use on the host "telnet localhost 5555", you connect to the guest telnet server.

[/HTML]

and then a little further past that it says ...

[HTML]
Note: Legacy stand-alone options -tftp, -bootp, -smb and -redir are still processed and applied to -net user. Mixing them with the new configuration syntax
           gives undefined results. Their use for new applications is discouraged as they will be removed from future versions.
[/HTML]

This suggests that -redir should not be used in the qemu command line and -net user, hostfwd= ... should be used instead.  Can anybody tell me the correct way of adding the hostfwd arguments into the virsh domain xml file?  Would I just do it the same way that is described in the link above?  Can anybody confirm if this is the correct way, or if there is a better way?

Many thanks - JB

---

