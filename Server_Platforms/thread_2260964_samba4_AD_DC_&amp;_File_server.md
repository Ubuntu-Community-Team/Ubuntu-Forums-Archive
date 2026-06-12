---
title: "samba4 AD DC &amp; File server"
date: 2015-01-15
forum: Server Platforms
---

### Post by Swiftjay on 2015-01-15
Would like a general opinion this wiki would be quite old: [https://wiki.samba.org/index.php/Samba_AD_DC_HOWTO](https://wiki.samba.org/index.php/Samba_AD_DC_HOWTO)

But they say as of that writting that it's not recommended to have the AD DC and File server on the same server, they should be separate.  

Is this still the case?  I'm asking this as I would like to know if I need to think about setting up VMs for clients in the near future if I'm to bring them into Linux and I'm sure Samba4 has come a long way to hopefully be able to handle both roles by now, but I could be wrong.  Anyone who has been testing/using samba4 with it's latest updates your input would be greatly appreciated.

Regards,
James

---

### Post by lingpanda on 2015-01-15
> **Swiftjay said:**
> Would like a general opinion this wiki would be quite old: [https://wiki.samba.org/index.php/Samba_AD_DC_HOWTO](https://wiki.samba.org/index.php/Samba_AD_DC_HOWTO)

But they say as of that writting that it's not recommended to have the AD DC and File server on the same server, they should be separate.  

Is this still the case?  I'm asking this as I would like to know if I need to think about setting up VMs for clients in the near future if I'm to bring them into Linux and I'm sure Samba4 has come a long way to hopefully be able to handle both roles by now, but I could be wrong.  Anyone who has been testing/using samba4 with it's latest updates your input would be greatly appreciated.

Regards,
James

It is still suggested **not** to use Samba4 as a DC and File Server together. This is from the Samba devs and personal experience.

---

### Post by Swiftjay on 2015-01-16
I wonder when this will improve to a level where it's acceptible for both.

I take it AD DC server is a PDC and then the file server simply joins the domain so it has a list of active users etc and does the shares using samba4?

---

### Post by lingpanda on 2015-01-16
> **Swiftjay said:**
> I wonder when this will improve to a level where it's acceptible for both.

I take it AD DC server is a PDC and then the file server simply joins the domain so it has a list of active users etc and does the shares using samba4?

I believe Samba 4.2 may be when it's acceptable for both. In a small environment with a single DC it's ok to run both services. It only becomes and issue when replicating across multiple DC's and sites.

PDC terminology should only be used when referencing an NT4 domain. Samba can be both a NT4 and ADDC domain. In a NT4 domain you have PDC and BDC. In a ADDC environment all DC's are equal. Apart from the FSMO roles. I'm simplifying it a bit. 

You will need to assign users or groups in AD a UID or GID when setting up a member server. Your member server will not know your users without one. It's all in the Samba wiki. I can assist if you decide to setup one. I recently setup one with help from the Samba mailing list.

---

### Post by Swiftjay on 2015-01-17
Can't non master AD DC servers set up users to  like in a windows forest or is this tied to the master AD DC server?  4.2 sounds good, I work mostly with small organisations and charities so I'm trying to think of the best alternatives if for now that's the case then fine.

Thanks for the advice I might take you up on that later on in the future, I haven't really played around with samba 4 yet but as things start developing for it and it's improving we will need to start going itno the deep end of things to get the best services and support in a Small and medium size Linux environment.

*edit*
Hopefully Ldap will soon be a thing of the past although I won't hold my breath for a good few years.

---

### Post by darkod on 2015-01-17
Similar like in a Windows AD, there is actually no master or slave DC. So you can create users on any DC unless you install it as read only (RODC). Samba4 offers the option of RODC like in windows and the rules are the same, you can't create users on RODC, it just replicates from other DCs.

Like mentioned before, there will be a difference between DCs in the FSMO roles but again that's similar to windows because a particular role is only on one specific DC, it can't be on more than one (the same role). But for user creation and management, you can do it on any DC.

---

