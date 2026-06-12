---
title: "UEC  euca-describe-availability-zones verbose command"
date: 2011-03-31
forum: Ubuntu Cloud and Juju
---

### Post by shahin on 2011-03-31
Seems I get an error about one of the python scripts.  I have removed and installed "python-image-store-proxy" and rebooted the machine.  But it did not work.  Here is the parse error I get: 
```

Traceback (most recent call last):
  File "/usr/bin/euca-describe-availability-zones", line 103, in <module>
    main()
  File "/usr/bin/euca-describe-availability-zones", line 99, in main
    euca.display_error_and_exit('%s' % ex)
  File "/usr/lib/python2.6/dist-packages/euca2ools/__init__.py", line 1091, in display_error_and_exit
    dom = minidom.parseString(msg)
  File "/usr/lib/python2.6/xml/dom/minidom.py", line 1928, in parseString
    return expatbuilder.parseString(string)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 940, in parseString
    return builder.parseString(string)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 223, in parseString
    parser.Parse(string, True)
xml.parsers.expat.ExpatError: mismatched tag: line 42, column 2

```
Has anyone else run into similar issue?

---

