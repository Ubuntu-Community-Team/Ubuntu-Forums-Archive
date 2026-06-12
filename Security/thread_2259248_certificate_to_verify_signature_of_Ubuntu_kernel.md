---
title: "certificate to verify signature of Ubuntu kernel"
date: 2015-01-03
forum: Security
---

### Post by robertchenxyz on 2015-01-03
[COLOR=#000000][FONT=Arial]https://wiki.ubuntu.com/SecurityTeam/SecureBoot mentions that Ubuntu (14.04) kernel is signed with "Canonical Ltd. Secure Boot Signing" key. Where can I find its corresponding certificate for verification purpose? That is, where can I to find the certificate file to make :[/FONT][/COLOR]
> sbverify --cert <cert> /boot/vmlinuz-3.13.0-24-generic.efi.signed
[COLOR=#000000][FONT=Arial]Signature verification OK?

[/FONT][/COLOR]

---

### Post by oldfred on 2015-01-03
Is it not in the instructions on the page you posted?

[https://wiki.ubuntu.com/SecurityTeam/SecureBoot](https://wiki.ubuntu.com/SecurityTeam/SecureBoot)

To verify Ubuntu signature on the signed kernel, you  must first extract the signature from the kernel image, then > use  sbverify to verify the image with the detached signature (must first  create the PEM certificate chain, above): 

$ sbattach --detach /tmp/vmlinuz-3.5.0-27-generic.efi.signature \
  /boot/vmlinuz-3.5.0-27-generic.efi.signed
$ sbverify --cert ~/keys/canonical-master-signing-public-chain.pem \
           --detached /tmp/vmlinuz-3.5.0-27-generic.efi.signature \
           /boot/vmlinuz-3.5.0-27-generic.efi.signed 
Signature verification OK


---

### Post by robertchenxyz on 2015-01-03
Thanks!
Yes, I can find the canonical certificate from [sb-setup and keys/]("http://bazaar.launchpad.net/~ubuntu-bugcontrol/qa-regression-testing/master/view/head:/notes_testing/secure-boot")[COLOR=#333333][FONT=Ubuntu Beta] mentioned on the page.[/FONT][/COLOR]

> wget [http://bazaar.launchpad.net/~ubuntu-bugcontrol/qa-regression-testing/master/download/head:/canonicalmasterpubli-20121127224415-zwfgigzh3kstgk0g-3/canonical-master-public.der](http://bazaar.launchpad.net/~ubuntu-bugcontrol/qa-regression-testing/master/download/head:/canonicalmasterpubli-20121127224415-zwfgigzh3kstgk0g-3/canonical-master-public.der)
> openssl x509 -inform der -in canonical-master-public.der -outform pem -out canonical-master-public.pem
> sbverify --cert x.pem /boot/vmlinuz-3.13.0-24-generic.efi.signed
Signature verification OK

---

