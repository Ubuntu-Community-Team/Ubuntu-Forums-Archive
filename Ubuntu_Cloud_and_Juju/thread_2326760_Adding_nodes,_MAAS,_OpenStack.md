---
title: "Adding nodes, MAAS, OpenStack"
date: 2016-06-04
forum: Ubuntu Cloud and Juju
---

### Post by Altino_Coelho on 2016-06-04
Hi,
I'm trying adding nodes to my maas, when trying log in with the API key I get this error:
> 

                                                     Traceback (most recent call last):            
              File "/usr/lib/python2.7/runpy.py", line 162, in _run_module_as_main            
                "__main__", fname, loader, pkg_name)            
              File "/usr/lib/python2.7/runpy.py", line 72, in _run_code            
                exec code in run_globals            
              File "/usr/lib/python2.7/dist-packages/maascli/__main__.py", line 20, in <module>            
                main()            
              File "/usr/lib/python2.7/dist-packages/maascli/__init__.py", line 29, in main            
                locale.setlocale(locale.LC_ALL, "")            
              File "/usr/lib/python2.7/locale.py", line 579, in setlocale            
                return _setlocale(category, locale)            
            locale.Error: unsupported locale setting             

I'm trying follow [this documentation]("https://maas.ubuntu.com/docs/maascli.html#api-key").
Thank you

---

