---
title: "SCRIPT_URI missing"
date: 2007-02-13
forum: Server Platforms
---

### Post by jtc on 2007-02-13
Right now I'm having some small issues with a rather fresh Edgy server.

Apache2 doesn't seem to want to give me the variables SCRIPT_URI and SCRIPT_URL. When I try to access $_SERVER['SCRIPT_URI'] from a script it returns nothing and when running phpinfo() they are not listed.

Mod_rewrite is loaded and is otherwise working fine.

Google seems to indicate that otherwise might have this problem, but I can't seem to find any solution. There are some mentions about mod_ssl, which don't apply in my case.

---

### Post by jtc on 2007-02-14
It seems as if the environment variables named SCRIPT_URL and SCRIPT_URI only are created by "RewriteEngine On" when it is in the <Virtualhost ...> scope. Oh well, you learn something new every day.

---

