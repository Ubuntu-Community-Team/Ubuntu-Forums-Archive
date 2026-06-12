---
title: "Autopilot Unity Tests - a more convenient way?"
date: 2012-12-04
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2012-12-04
I have worked out a method for running those 461 Autopilot Unity tests in batches with a command argument that posts the results into a log file. The tutorial is here. Click on the Autopilot Unity Tests link to go down the page.

[https://wiki.ubuntu.com/U+1/activities#Autopilot_Unity_Testing]("https://wiki.ubuntu.com/U+1/activities#Autopilot_Unity_Testing")

I find this more convenient than running the tests one at a time or all at once. Which were the only options.

For example, this command will run five tests.

```
autopilot run -o . unity.tests.launcher.test_capture
```

and this command will run 30 tests.

```
autopilot run -o . unity.tests.test_panel.PanelWindowButtonsTests
```

That one is untested by me but it should work. So, far I have run 33 of the 57 batches. I am working my way from the smallest batch to the largest batch, the 30 tests batch.

Update: I have just completed all the batch tests. It takes something like 1 hour 45 minutes. This is longer than running the tests all at once but I can stop and start whenever I like and I do have some idea of where I am in the test series.

Regards.

---

### Post by ventrical on 2012-12-04
> **grahammechanical said:**
> I have worked out a method for running those 461 Autopilot Unity tests in batches with a command argument that posts the results into a log file. The tutorial is here. Click on the Autopilot Unity Tests link to go down the page.

[https://wiki.ubuntu.com/U+1/activities#Autopilot_Unity_Testing](https://wiki.ubuntu.com/U+1/activities#Autopilot_Unity_Testing)

I find this more convenient than running the tests one at a time or all at once. Which were the only options.

For example, this command will run five tests.

```
autopilot run -o . unity.tests.launcher.test_capture
```and this command will run 30 tests.

```
autopilot run -o . unity.tests.test_panel.PanelWindowButtonsTests
```That one is untested by me but it should work. So, far I have run 33 of the 57 batches. I am working my way from the smallest batch to the largest batch, the 30 tests batch.

Update: I have just completed all the batch tests. It takes something like 1 hour 45 minutes. This is longer than running the tests all at once but I can stop and start whenever I like and I do have some idea of where I am in the test series.

Regards.


Thanks Graham  .. your method is a lot more efficient , so. no down time really.

Regards,
Ventrical

---

