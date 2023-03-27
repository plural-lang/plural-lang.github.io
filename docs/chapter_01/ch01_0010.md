# TEST 01

## Setup

UPDATE 333

Assume

- $n$ sample data points $X_i$, where $i\in\{0,1,\dots, (n-1)\}$,
- from an underlying probability density $f(x)$ (and cumulative distribution function $F(x)$).

$$\begin{aligned}
\int k(x)\,dx&=1\\
k(-x)&=k(x)\\
\int x^2\,k(x)\,dx&=1
\end{aligned}$$

MORE TEXT

$$\operatorname{MISE} (h) = \mathbb{E}\!\left\{\, \int \left[\hat{f}_h(x) - f(x)\right]^2 \, dx \right\}$$

|Issue|Solution / mitigation|Notes
|:---|:---|:---
|1. KDE doesn't characterise the distribution (because it requires that we store the original samples).| Resample the *smoothed* distribution.|Need the relevant C# `class`to distinguish whether the data is original sample or smoothed.|
|2. KDE distorts the variance, which is a key risk measure.|Explicitly correct for the increase in variance -- see below.|Implicit assumption that this does not distort the distribution. <br/>I *think* we are assuming at least symmetry (which would not be true e.g. for log-normals).|
|3. KDE tails are asymptotically $\exp(-(x/h)^2)$, i.e. the tail depends on $h$, not the actual tail shape.|Not sure -- some thoughts set out below.|It is dangerous to make assumptions about the tails (including whether the tails on either side are similar.|

