---
title: "Radius auth proxy Multi factor"
date: 2017-12-13
forum: Security
---

### Post by rtlucht1978 on 2017-12-13
I am trying to set up an auth proxy so that I can log into a device with radius using Google Authenticator and a user and password from another radius server tied to active directory.  I want my user and password with google pin number to go to the authentication proxy there the user and pin are confirmed then the username and password go to the second radius server then are confirmed with active directory.  We are attempting to setup up dual factor authentication into devices through radius.  The second radius server is a CISCO ISE server that will dictate the amount of access based on your Active Directory account.  I want the first part so we can have the multi-factor piece in there.  I am looking into FreeRadius and setting up some labs.  I would like to use Google authenticator to test the theory.  Looking for any help, thanks.

---

