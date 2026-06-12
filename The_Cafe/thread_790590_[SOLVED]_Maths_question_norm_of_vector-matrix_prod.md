---
title: "[SOLVED] Maths question: norm of vector-matrix product"
date: 2008-05-11
forum: The Cafe
---

### Post by urgnom on 2008-05-11
Hi. I don't have my college text books at hand and I need to know the following:

Is there some relationship corresponding to the Cauchy-Schwarz inequality for matrix-vector products? Take the 2-norm of Ax, can I then write

||Ax|| \leq ||A|| ||x||, 
where the vector norm is used for x and the vector-induced norm is used for the matrix A? (2-norm)? 

I'd really appreciate an answer to this :-) :popcorn:

---

### Post by Erik Trybom on 2008-05-11
Yes, according to my mathematics handbook you can. (BETA, Råde/Westergren, p380.)

---

### Post by bite on 2008-05-11
> **urgnom said:**
> Hi. I don't have my college text books at hand and I need to know the following:

Is there some relationship corresponding to the Cauchy-Schwarz inequality for matrix-vector products? Take the 2-norm of Ax, can I then write

||Ax|| \leq ||A|| ||x||, 
where the vector norm is used for x and the vector-induced norm is used for the matrix A? (2-norm)? 

I'd really appreciate an answer to this :-) :popcorn:

If by 2-norm you mean p-norm with p=2, that is, sqrt(x_1^2+..+x_n^2), then the inequality is implicit in the definition of the p-norm for the matrix. I get from Golub+VanLoan, Matrix Computations, §2.3, that:

||A||_p=sup_{x!=0} ||Ax||_p/||x||_p

therefore ||Ax||_p <= ||A||_p ||x||_p, isn't it?

---

### Post by urgnom on 2008-05-11
Thx, guys. I assumed it was correct, and got my very nice convergence result :-) Testing it on some examples right now :-):guitar:

---

