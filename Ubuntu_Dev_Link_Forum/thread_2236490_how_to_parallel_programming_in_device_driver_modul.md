---
title: "how to parallel programming in device driver module"
date: 2014-07-27
forum: Ubuntu Dev Link Forum
---

### Post by zerop2 on 2014-07-27
how to parallel programming in device driver module

/home/wonder/layer/hello.c:608:5: error: implicit declaration of function &#8216;MPI_Init&#8217; [-Werror=implicit-function-declaration]
/home/wonder/layer/hello.c:609:5: error: implicit declaration of function &#8216;MPI_Comm_rank&#8217; [-Werror=implicit-function-declaration]
/home/wonder/layer/hello.c:609:26: error: &#8216;MPI_COMM_WORLD&#8217; undeclared (first use in this function)
/home/wonder/layer/hello.c:609:26: note: each undeclared identifier is reported only once for each function it appears in
/home/wonder/layer/hello.c:610:5: error: implicit declaration of function &#8216;MPI_Comm_size&#8217; [-Werror=implicit-function-declaration]
/home/wonder/layer/hello.c:615:5: error: implicit declaration of function &#8216;MPI_Finalize&#8217; [-Werror=implicit-function-declaration]

can not use normal functions after include <linux/mpi.h>
```

int my_id = 0;
    int num_procs = 0;
    int ierr = MPI_Init(2, 0);
    ierr = MPI_Comm_rank(MPI_COMM_WORLD, &my_id);
    ierr = MPI_Comm_size(MPI_COMM_WORLD, &num_procs);
    if(my_id == 0){
    }
    else if(my_id == 1){
    }
    ierr = MPI_Finalize();


```

---

