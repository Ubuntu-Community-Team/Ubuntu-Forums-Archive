---
title: "Warty Backport: bmp-extra-plugins"
date: 2005-02-13
forum: Ubuntu Backports
---

### Post by rufius on 2005-02-13
**Synopsis**
Per user request I manually debianized a cvs release of the plugins.

**Backporting Process**
The source came from the original developer and was debianized. Build went without errors, but was rebuilt because of a negligence of the description for the package.

**Packaging Status:**
i386 -- Staging at revision 27
amd64 -- Not packaged
ppc -- Not packaged

**Beta tester notes:**
Works flawlessly with all tested media.

---

### Post by techn9ne on 2005-02-14
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  bmp-extra-plugins: Depends: libglib2.0-0 (>= 2.6.0) but 2.4.7-0ubuntu2 is to be installed
E: Broken packages

---

### Post by rufius on 2005-02-14
[QUOTE=techn9ne]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  bmp-extra-plugins: Depends: libglib2.0-0 (>= 2.6.0) but 2.4.7-0ubuntu2 is to be installed
E: Broken packages[/QUOTE]
 Odd, I'm looking into it now.

<edit>
Accidently built with glib2.0 2.6 installed on my system and was unaware of the glib2.0 >= 2.6 dependency. I'm in the process of talking with jdong about how to resolve it.
</edit>

<edit2>
I'm working to resolve the issue as we speak.
</edit2>

---

### Post by rufius on 2005-02-14
All issues have been resolved and glib2.0 (2.6.2) is now available for download from the repository.

---

### Post by techn9ne on 2005-02-15
Works great for me now.

---

### Post by rufius on 2005-02-15
[QUOTE=techn9ne]Works great for me now.[/QUOTE]
 Great :-D

---

### Post by Technoviking on 2005-02-15
The plugins work great for me other than wmdiscotux, which crashes in full screen mode.

Mike

---

### Post by rufius on 2005-02-15
[QUOTE=Mike Basinger]The plugins work great for me other than wmdiscotux, which crashes in full screen mode.

Mike[/QUOTE]
 Heh, I forgot to test the visual plugins. I wasn't even aware people used those ;)

---

