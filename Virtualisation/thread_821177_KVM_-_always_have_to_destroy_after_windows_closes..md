---
title: "KVM - always have to destroy after windows closes..?"
date: 2008-06-06
forum: Virtualisation
---

### Post by hopelessone on 2008-06-06
Hi,

After windows shuts down and says safe to turn off...I try clicking on the "Shutdown" button but nothing happens and always have to select "destroy"...

how can i fix this?

Thanks

---

### Post by ktulu73 on 2008-06-07
This is because Virtmanager disable acpi for Windows Guest by default.
To enable acpi for your Windows guest, you can add the following lines to the guest's xml:
```
<features>
    <acpi/>
  </features>
```

But this will increase the cpu load to 100 percent for the guest, so it's disabled by default.

---

### Post by hopelessone on 2008-06-07
ok thanks...

so the CPU is 100% all the time? or only when on shutdown? is it ok to keep using the "destroy" when shutdown?

Thanks a bunch for the info!!

---

