---
title: "OpenVPN Server/Client Certificates"
date: 2009-01-05
forum: Security
---

### Post by brian_hayward on 2009-01-05
I am trying to configure my Ubuntu box as a VPN server using OpenVPN.  I have created myself a CA for signing certificates used to authenticate server/client connections.  However when it comes time for me to create these certificate/key pairs do i need to enter the same Distinguised Name parameters (eg. countryName, stateOrProvinceName, etc) in the server/client certificate/key pairs that i entered when i created my CA certificate?  For example when i created my CA certificate i entered CA for my stateOrProvinceName, and US for my countryName.  Do i need to enter CA, and US in the server/client certificates for each to work properly?

---

