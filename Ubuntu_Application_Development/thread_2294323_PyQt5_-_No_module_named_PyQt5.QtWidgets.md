---
title: "PyQt5 - No module named PyQt5.QtWidgets"
date: 2015-09-10
forum: Ubuntu Application Development
---

### Post by swatto on 2015-09-10
Good Evening,

I am running Ubuntu 15.04 and I have installed Qt Creator from the Ubuntu Software Centre.  I am trying to run a small Python script to show a Window:

```
import sys
from PyQt5.QtWidgets import QApplication, QDialog
from ui_imagedialog import Ui_ImageDialog

app = QApplication(sys.argv)
window = QDialog()
ui = Ui_ImageDialog()
ui.setupUi(window)

window.show()
sys.exit(app.exec_())
```

but I get the following error:

> 
Traceback (most recent call last):
  File "ui.py", line 2, in <module>
    from PyQt5.QtWidgets import QApplication, QDialog
ImportError: No module named PyQt5.QtWidgets


I am unsure why this is, please can you help?

Thanks,

---

### Post by spjackson on 2015-09-13
You will get that error if pyqt5 isn't installed. So install either the python-pyqt5 or python3-pyqt5 package depending on which python version you are using.

---

