---
title: "The one good feature of Internet Explorer"
date: 2008-04-29
forum: The Cafe
---

### Post by Mateo on 2008-04-29
The browser that can-do-no-right does do one thing right.  When you come across a table you can right-click and select "Export to Excel", and an Excel spreadsheet will load with the table.  It's fantastic.  If they had a similar feature/extension for CSV in Firefox or Epiphany, that would be killer.  Get on it, Mozilla and Gnome.

---

### Post by jken146 on 2008-04-29
Copy & paste works with OpenOffice.  The table gets formatted in Writer as a table.  I haven't tried it in Calc though.

---

### Post by Posterus on 2008-04-29
> **jken146 said:**
> Copy & paste works with OpenOffice.  The table gets formatted in Writer as a table.  I haven't tried it in Calc though.

rofl as i was reading his post i was thinking "copy and paste" haha

---

### Post by LaRoza on 2008-04-29
> **Mateo said:**
> The browser that can-do-no-right does do one thing right.  When you come across a table you can right-click and select "Export to Excel", and an Excel spreadsheet will load with the table.  It's fantastic.  If they had a similar feature/extension for CSV in Firefox or Epiphany, that would be killer.  Get on it, Mozilla and Gnome.

MS provides IE and Excel, of course that want to promote their own apps. Does IE export to CSV? Does it export to Calc? Gnuemeric?

Opera 9.50b2. Highlighting table, and right clicking gives option to copy to note (which is handy). Highlighting the table, and middle clicking in Calc gives option to import. 

It works fine.
From: [http://en.wikipedia.org/wiki/Largest_counties_of_the_united_states](http://en.wikipedia.org/wiki/Largest_counties_of_the_united_states)

[http://www.box.net/shared/pfhste4o40](http://www.box.net/shared/pfhste4o40)

---

### Post by smoker on 2008-04-29
> **Mateo said:**
> ..  When you come across a table you can right-click and select "Export to Excel", and an Excel spreadsheet will load with the table...

doesn't excel run macros? this sounds like an easy way to infect a windows computer!

---

### Post by Mateo on 2008-04-29
> **LaRoza said:**
> MS provides IE and Excel, of course that want to promote their own apps. Does IE export to CSV? Does it export to Calc? Gnuemeric?

The format is irrelevant.  It can easily be converted.  The fact that it has such a feature to export to a spreadsheet is nice.  Firefox doesn't have this ability.

Copy and paste is, of course, what I do.  But it doesn't work nearly as well IMO.  Formatting screws up and you get URLs that are followed (unwanted by me).

---

### Post by LaRoza on 2008-04-29
> **Mateo said:**
> The format is irrelevant.  It can easily be converted.  The fact that it has such a feature to export to a spreadsheet is nice.  Firefox doesn't have this ability.

Copy and paste is, of course, what I do.  But it doesn't work nearly as well IMO.  Formatting screws up and you get URLs that are followed (unwanted by me).

Well, IE and Excel are MS. They go very well together. The free alternatives don't try to force you do use a single app. 

Epiphany, the GNOME browser, could open in Gnumeric, as they are both GNOME apps I guess. Opera allows you to choose what app to open it in.

---

### Post by swoll1980 on 2008-04-29
Compatibility is the best feature of IE, and the only reason I still have Windows xp installed on my Computer

---

### Post by tempest on 2008-04-29
A firefox plugin could probably do this without too much trouble. Just need to export it to csv. I have not done a plugin search for this, so I'm not sure if one is available or not.

---

### Post by LaRoza on 2008-04-29
> **tempest said:**
> A firefox plugin could probably do this without too much trouble. Just need to export it to csv. I have not done a plugin search for this, so I'm not sure if one is available or not.

It would be easy to write a script to do it, I could to it, but I never wrote a Firefox plugin so I don't don't know if it would work that way.

---

### Post by klange on 2008-04-29
One could write a javascript function to do it... I'll get right on that after I look at some things in a C-F plugin for future reference.

---

### Post by klange on 2008-04-29
Not very polished, but slap this into the address bar and it'll print a CSV for the first table (you can change the index in the function to get another table):
```
function exportCSV(theTable) {
var trs = theTable.getElementsByTagName('tr');
var csv = '';
var i, j, tds;
for (i = 0; i < trs['length']; i++) {
 tds = trs[i].getElementsByTagName('td');
 for (j = 0; j < tds['length']; j++) {
  csv = csv + tds[j].innerHTML + ',';
 }
 csv = csv.substring(0,csv.length-1) + '\n';
}
return csv;
}
document.write(exportCSV(document.getElementsByTagName('body')[0].getElementsByTagName('table')[0]));
```

---

