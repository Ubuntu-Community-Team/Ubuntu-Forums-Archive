---
title: "Destroy guest OS using php"
date: 2012-03-25
forum: Virtualisation
---

### Post by AleeRaza on 2012-03-25
I am using libvirt-php to manage my virtual machines.  I need to shutdown/destroy domU.  For this I used the following php script: 

 < ? php $conn=libvirt_connect("xen:///");     $name=libvirt_domain_lookup_by_id($conn,4);
    $dest=libvirt_domain_destroy($name);
    echo $dest; ?> When I run this on xampp server the output: 

Warning:  libvirt_domain_destroy() [function.libvirt-domain-destroy]: operation  virDomainDestroy forbidden for read only access in  /opt/lampp/htdocs/xampp/byname.php on line 5. ?????????? Anyone know??
  Here is the documentation: [http://libvirt.org/php/api-reference.html#libvirt_domain_destroy](http://libvirt.org/php/api-reference.html#libvirt_domain_destroy)

---

### Post by nothingspecial on 2012-03-27
*Thread moved to **Virtualization**.*

---

