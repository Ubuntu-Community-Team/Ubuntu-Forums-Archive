---
title: "No Client Access to Test Page of Shared Printer on a Server"
date: 2021-05-21
forum: Server Platforms
---

### Post by penguin-fach on 2021-05-21
Server - Ubuntu 20.04 LTS with LXDE frontend
Clients - Kubuntu 20.04 LTS

When setting up a printer on the server, the printer test page is restricted to root. It is necessary to unlock CUPS in order to complete setup. This creates a problem when setting up client printer access since any attempt to print a test page or printer diagnostics from a networked client device, to the shared server printer, gets a non-explicit 'permission denied' warning, which can look like a driver installation or user config problem.

Once this is understood it is simply irritating rather than a technical problem since any test document can be printed instead, but can anyone tell me the rationale behind preventing client devices from printing test pages?

---

### Post by SeijiSensei on 2021-05-26
Probably it's a security feature.  Suppose this printer was serving a hundred users, and one of them decided it would be "fun" to keep sending test pages to the printer. Because so many people use Linux these days solely as a desktop client, it's hard to imagine the kinds of issues people administering large networks face. Often security models in the *nix world start from those usage cases.

---

