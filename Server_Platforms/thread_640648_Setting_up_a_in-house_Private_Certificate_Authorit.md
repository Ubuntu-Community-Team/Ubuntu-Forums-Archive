---
title: "Setting up a in-house Private Certificate Authority CA"
date: 2007-12-14
forum: Server Platforms
---

### Post by rrolsbe on 2007-12-14
I have spent quite a bit of time trying to find documentation on setting up apache to serve up client CSR's "Certificate Signing Request".  I have  found considerable information on how to configure apache for SSL.  I have apache configured for SSL and have generated a self signed root certificate.  From the client, I can install this root certificate using Firefox and an https connection to the server; however, I would like to make a CSR request from my client machine(s) to this same server.  Can anyone point me to any configuration documentation outlining how to configure my "Private CA" to sign CSR requests from clients?  Basically I want  my own private Verisign.  I would like my clients to be able generate asymmetric key pairs, send only the public portion of the key pair to my "Private" CA server which then returns the signed certificate to the requesting client.     I would like to perform this via an https CSR request from my clients to an appropriately configured apache server.  ADDITIONAL CLARIFICATION:  I found the openssl command-line instructions outlining how to generate a CSR on the client and sign at the CA; however, I really need to serve a web form over https to the client similar to the way Verisign, CaCert and others do.

I am using ubuntu 7.04 Fiesty

Any guides outlining the entire configuration, describe above, would be my first choice but I definitely need help configuring the apache server to serve up the CSR requests.

Thanks Very Much In Advance
Regards
Ron

---

