---
title: "OpenDJ: Cannot delete missing attibutes"
date: 2018-03-02
forum: Server Platforms
---

### Post by tbd2 on 2018-03-02
We are getting recurring errors in Apache Studio:


ERR_04228 Parser failure on attribute type description:
( attr-test-id NAME 'attr-test-id' DESC 'attr test id' 
EQUALITY 2.5.0.2 ORDERING 1.3.6.1.4.1.42.2.0.9.4.3.1 SUBSTR 2.5.0.4 
SYNTAX 1.3.6.1.4.1.1466.115.0.1.15 USAGE userApplications X-APPROX 
'1.3.6.1.4.1.0.1.4.1' X-APPROX '1.3.6.1.4.1.0.1.4.1' X-SCHEMA-FILE '111-user.ldif' )
Antlr message: X-APPROX appears twice.
Antlr column: 230

These attributes no longer exist in the schema. When we try to delete these attributes is says it is attached to an object (my-custom-object).
When we try to delete 'my-custom-object' is says we have these attributes associated with it. Seriously?

Where do we go from here?

---

### Post by tbd2 on 2018-03-05
bump

---

