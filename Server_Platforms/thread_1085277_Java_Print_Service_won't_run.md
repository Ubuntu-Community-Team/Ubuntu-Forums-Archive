---
title: "Java Print Service won't run"
date: 2009-03-02
forum: Server Platforms
---

### Post by ali irawan on 2009-03-02
I have some problem with my latest project.
I develop a web based application based on Java platform, using JSF. I use uBuntu 8.10 for the Operating System.

The web application would show list of available Print Service
in a DropDownList.

    ```
public SelectItem[] getPrintServiceList() {
        SelectItem[] arr = null;

        PrintService[] service = PrintServiceLookup.lookupPrintServices(null, null);
        System.out.println(service.length);
        arr = new SelectItem[service.length];
        for (int i = 0; i < service.length; i++) {
            System.out.println(service[i].getName());
            arr[i] = new SelectItem(service[i].getName(), service[i].getName());
        }
        return arr;
    }
```


But what happen... the list won't show. The weird things i do test deploy the same application in Windows platform and it works!

I have tried to create a simple application (Console based), to use lookupPrintService method, and it works. it shows all printer that has been set up in CUPS.

Output:
Canon
Tally

But why it won't show in Web Application (in DropDownList).
Any body can help me.

Below i attach what should shown in Windows platform. It list all available printers. but when i deply on uBuntu, it doesnt work.

Is there any issue how to get Java Print correctly (j2ee applications) in uBuntu platform.

---

### Post by fabou3377 on 2009-11-15
Have you find a solution? By me I found printers but the media name aren't correct...

---

