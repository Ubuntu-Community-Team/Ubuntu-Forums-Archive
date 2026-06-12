---
title: "Anyone noticed this from:-  Processing triggers for libglib2.0-0"
date: 2012-01-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by philinux on 2012-01-16
I see this. 

/usr/share/glib-2.0/schemas/com.canonical.Unity.gschema.xml: Error on line 56 char 1: <schema id='com.canonical.Unity.Runner'> already specified.  This entire file has been ignored.

[edit] purged and reinstalled unity unity-2d and ubuntu-desktop

---

### Post by effenberg0x0 on 2012-01-16
Hi Phil,

+1

---

### Post by philinux on 2012-01-16
> **effenberg0x0 said:**
> Hi Phil,

+1

Ah ok not just me then. It seems trivial now I've looked at the file. This is line 55 to 61. It looks similar to other sections of the file too.

```
<schema path="/desktop/unity/runner/" id="com.canonical.Unity.Runner" gettext-domain="unity">
    <key type="as" name="history">
        <default>[]</default>
        <summary>History of Alt + F2 command</summary>
        <description>Key for storing the history of the Alt + F2 command.  </description>
    </key>
  </schema>

```

---

