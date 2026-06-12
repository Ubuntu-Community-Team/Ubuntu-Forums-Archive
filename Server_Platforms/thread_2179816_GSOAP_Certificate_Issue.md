---
title: "GSOAP Certificate Issue"
date: 2013-10-10
forum: Server Platforms
---

### Post by shandinesh on 2013-10-10
hi all,

 I have my own Gsoap application .exe file, i got the certificate verify failed issue on running my application,

I am getting the following error while sending the request.

[B]"SSL_ERROR_SSL
error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed"[/B]

I tried both **SOAP_SSL_NO_AUTHENTICATION** and **SOAP_SSL_DEFAULT**

options for soap_ssl_client_context() calls. In the case of second option I actually

made the required certificates on the client side.

  Now it looks like there are certificates to be exchanged and verified as part

of SSL handshake.
***SOAP_SSL_NO_AUTHENTICATION** disables server authentication for *

*[I]testing purposes. But this assumes  the server does not require clients to authenticate. Now since this call fails, I am assuming that the Server here*
[/I]
[I][I]actually require the client to authenticate and I know from Srikanth that 
we don't have a valid server certificate for cost reasons. Is there anyway
[/I][/I]
[I][I]for this validation requirement to be turned off at the server end ?
[/I][/I]
[I][I]Otherwise, we may need valid certificates at the server end so that the
[/I][/I]
[I][I]transaction goes through.
[/I][/I]
[I][I]  Just to be sure, I tried **SOAP_SSL_DEFAULT** option with valid client side 
[/I][/I]
[I][I]certificates. This too fails with the same error. 
**

   Please help to resolve this issue. Since I am new to the domain I may be
[/I][/I]

*[I]*[/I]
[I][I]missing something. In that case please guide.

Thanks,
shan
[/I][/I]
*[I]*[/I]

---

