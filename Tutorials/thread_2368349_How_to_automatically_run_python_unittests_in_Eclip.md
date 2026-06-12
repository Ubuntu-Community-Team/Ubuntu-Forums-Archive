---
title: "How to automatically run python unittests in Eclipse"
date: 2017-08-09
forum: Tutorials
---

### Post by paulmilliken on 2017-08-09
Create a python script to run the unittests as follows (the first line is important):

```
#!/usr/bin/python

import unittest

from nose.plugins.collect import TestSuite
    
if __name__ == "__main__":
    testsuite = unittest.TestLoader().discover('.')
    unittest.TextTestRunner(verbosity=2).run(testsuite)
```

Change the permissions of the script to make it executable as follows:

```
chmod +x /path/to/python_script.py
```

In Eclipse, right-click on the project and go to "properties"

Click on the "builders" tab and create a new builder

In "location" type /path/to/python_script.py and in "working directory" browse the workspace to the folder where the script is.

Under "build options", select "During auto builds" and apply these changes.

Under the "project" menu make sure "build-automatically is selected"

Now when you save your unittests should run and output for example

```
Ran 22 tests in 0.001s

OK
```

---

