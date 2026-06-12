---
title: "Concerns about legacy Windows systems"
date: 2011-02-27
forum: Security
---

### Post by DrJohn999 on 2011-02-27
I'm concerned about the Windows (XP and 7) systems on the LAN -- a couple of laptops and several VMs that are needed to run for example legacy accounting or graphics apps, or Widows-only content from sites that don't support Linux versions of Flash or browsers. All of the OS's are kept patched and up-to-date. Locally they use a combination of A/V scanner and heuristic detection; Firefox, NoScript, AdBlock; restricted browser policies in Firefox and IE; on the laptops Windows (7 anyway) does a fair job of setting firewall policies per the connection type. On the mail server RBL, greylisting, SpamAsassin, and Clam filter incoming email. When the laptops go outside they are supposed to VPN back to the LAN as the web gateway, but that's not always possible at any particular external location.

I would love to tank the legacies and reduce my worries, but that's not practical (yet :>). Today my main concerns are:

1. Scripts injected onto apparently 'safe' web pages. I ran into one of these recently at another location. There, a proxy / filter appliance caught the malware (jscript at the top of the page, above <!Doctype...). Without a catch at the proxy level:

    -- NoScript doesn't work well for non-technical users who just select "Allow..." for every site. It presents a barrier for accidental access to malicious pages but effectiveness is only as good as the informed user who is willing to sit on the other side of the barrier and select what's allowed in.

     -- Which Windows A/V scanners locally (on access) identify malicious and/or obfuscated scripts inserted into web pages?

    -- Which Linux A/V scanners (e.g. Clam or other) are useful to scan incoming pages for such, alongside a proxy (such as Squid or other)?

2. What about compromised Windows systems accessing Samba shares with the Samba user's privileges?  What's to stop this one? Of course all the shares and everything else is backed up daily, but the potential compromise of the data is the real issue.

3. What else worries others who have to support Windows systems along these lines?

Thanks for any replies -- J.

---

