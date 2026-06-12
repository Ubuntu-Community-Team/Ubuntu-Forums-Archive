---
title: "Compiling LibVirt from scratch for esx driver support"
date: 2014-01-03
forum: Virtualisation
---

### Post by Theory5 on 2014-01-03
So I like to tote myself as an intermediate linux user. But occasionally i take on a side project of my own imagination, and I fall out of my depth. Today I was finishing setting up Cuckoo Malware Sandbox configured to run an ESXI server, but I ran into a problem. I need to recompile libvirt for use with the esx driver (further reading: [http://www.libvirt.org/drvesx.html](http://www.libvirt.org/drvesx.html)). So even though I have already installed LibVirt, I grabbed the source from Git to recompile. I followed all the instructions here: [http://libvirt.org/compiling.html](http://libvirt.org/compiling.html) (bottom of page at compile from Git checkout) but I am still getting the cuckoo error "Libvirt returned an exception on connection: unsupported configuration: libvirt was built without the 'esx' driver."

What I am missing? 

Please let me know if you need more information.

Thanks!

---

