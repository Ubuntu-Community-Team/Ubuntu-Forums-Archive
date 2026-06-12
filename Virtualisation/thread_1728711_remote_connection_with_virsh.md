---
title: "remote connection with virsh"
date: 2011-04-14
forum: Virtualisation
---

### Post by brandonroy on 2011-04-14
Hi, all. I choose ubuntu maverick server as my virtualization platform  with KVM as the hypervisor.I have deployed kvm in two machines A, B. Now  I want to try to use virsh in A to connect to B. So I configured the  certification support  following the instructions in this page    [http://libvirt.org/remote.html#Remote_certificates](http://libvirt.org/remote.html#Remote_certificates)  . 
Every time I run this command 'virsh -c remote://B ', it return a  connection failure information. Then in machine B(the server), I started  libvirtd daemon with --verbose and --listen options and it provided me  the error information 
 error : qemudClientReadBuf:1656 : gnutls_record_recv: A TLS packet  with unexpected length was received. 
When I googled about the problem, I found it was a bug of CentOS. So, is  it a bug in Ubuntu ? 
Regards

---

