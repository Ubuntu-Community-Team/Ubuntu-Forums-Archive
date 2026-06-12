---
title: "DataTable.Select method"
date: 2011-04-25
forum: Server Platforms
---

### Post by vippul on 2011-04-25
I am using MonoDevelop with SQL Server whenever I try to do use the Select method on the Datatable object the performance really detoriates it is 3 times slow than it is with .Net. Are there any work arounds?

---

### Post by dtfinch on 2011-04-25
What does your query look like? (I use ADO.NET on Windows, but not in Mono yet) If you're searching the primary key, and the DataTable.PrimaryKey property is set, you could also try .Rows.Find. Or for other single-row selects you could create a dictionary or hashtable of values to datarows and search that. .Select() is the slowest possible method because it has to do a full table scan and parse/evaluate the filter expression on each row.

This should probably be moved to a programming section.

---

