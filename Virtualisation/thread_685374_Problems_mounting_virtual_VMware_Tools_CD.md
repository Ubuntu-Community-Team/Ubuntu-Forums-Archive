---
title: "Problems mounting virtual VMware Tools CD"
date: 2008-02-02
forum: Virtualisation
---

### Post by Harrkev on 2008-02-02
Hi.

I got VMWare working just fins (a 2nd install of Gutsy running under Gutsy, for testing purposes).  Works great, except that I cannot install VMWare Tools

When I mount the VMware tools volume through the "Install VMWare Tools" option, the virtual CD is mounted.  However, when I look at it, the file names appear to be the contents of the files themselves.

For example, I am going to paste one part of a directory entry:

-r-xr-xr-x 1 root root 0 1945-05-27 10:05 e-specific escape characters (ask hpreg)
vmware_product_name() {
  echo 'vmware tools'
  exit 0

That is a pretty funny file name.
Obviously, there is not a single tarball around.  Any ideas on where to get the tools or how to get this to mount properly?

---

