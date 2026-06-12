---
title: "storing threads in a vector, c++"
date: 2013-05-19
forum: Ubuntu Application Development
---

### Post by 3v3rgr33n on 2013-05-19
How does one store threads in a vector in c++?

I currently have this.

```

std::vector<std::thread> threads;
threads.push_back(std::move(tmp));

```

Where tmp is a thread. This, however, creates a segmentation fault when trying to access
the thread again.

Please help

---

