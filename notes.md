# Background


### Basic Paley graphs and a bit graph theory
Reference on clique number of Paley graphs can be found in [C.H. Yip's Paper](https://open.library.ubc.ca/media/stream/pdf/24/1.0395514/3).

Let $\mathbb{F}_q$ be finite field of order $q$ where $q\equiv 1$ mod $4$ and $q$ a *prime power*. Any finite field is uniquely characterized by its order, which is either prime or a power of prime. (Read more [here](https://en.wikipedia.org/wiki/Finite_field), and also 13.1-13.2 of Dummit-Foote)

The **Paley graph** $G_q$ is the graph with $V(G_q)=\mathbb{F}_q$ and $E(G_q):=\{(i,j)| \exists x\in \mathbb{F}_q^{\times}$ s.t. $j-i=x^2\}\subset \mathbb{F}_q\times\mathbb{F}_q$, i.e., $i, j$ is connected iff their difference is a quadratic residue in $\mathbb{F}_q$. A $d$-Paley graph is the definition for Paley graph except we connect two nodes iff their difference is a $d$-th power residue and $q\equiv 1$ (mod $2d$).


##### Consequences:

0. We defined $q\equiv 1$ (mod $4$) so that the graph is un-directed.

1. For any $i\in \mathbb{F}_p$, where $p$ is prime such $q$ (in the above sense), $deg(i)= \frac{p-1}{2}$. 

 

Proof: WLOG, let $p$ be odd, $sq:\mathbb{F}_p^{\times} \to\mathbb{F}_p^{\times}$ be the squaring endomorphism, then the kernel is the subgroup $\{\pm 1\}$, hence $|Im(sq)|=\frac{|\mathbb{F}_p^{\times}|}{2}=\frac{p-1}{2}$. Now for any $i$, there are $\frac{p-1}{2}$ options to choose $j$, so that $i-j\in Im(sq)$. Hence $deg(i) =\frac{p-1}{2}$.


2. The above result can be extended for $\mathbb{F}_q$ for any prime power $q = p^k$.

3. $q\equiv 1$ (mod $4$) is needed so that the graph is un-directed.

4. [(L. Carlitz)](https://www.jstor.org/stable/2034798) Automorphism group of Paley graph $G_q$ is the set of maps $x\mapsto a^{\sigma} +b$ where $a\in (\mathbb{F}_q^{\times})^2, b\in\mathbb{F}_q$ and $\sigma=p^j$, where $0\leq j < k$ and $q=p^k$.

5. $G_q$ is self-complementary, i.e., isomorphic to its complement. For self-complementary graphs, clique number is equals to its coclique number.

Proof: Consider the set endomorphism $f$ on $\mathbb{F}_q$ given by $x\mapsto rx$ where $r$ is a quadratic non-residue. It defines a graph isomorphism making $P_q$ self-complementary. The second statement is trivial.

6. A graph is symmetric if its automorphism group acts transitively on its vertices and edges. Paley graphs are symmetric.

Proof: See [Lemma 2.2.5 of (C. Yep)](https://open.library.ubc.ca/media/stream/pdf/24/1.0395514/3)

7. Self-complementary and symmetric gives a bound on $\omega(G_q)$, which is $\sqrt{q}$. More generally, for any vertex-transitive graph $G$, $\omega(G)\alpha(G)\leq |V(G)|$, where $\omega(G)$ (resp. $\alpha(G)$) is the clique (resp. coclique) number. Using this on $G_q$ makes the result trivial. Without appealing to this result, we can use strongly regularity and quadratic character to prove this result. (See 8-12 below.)

8. A graph is $d$-regular if all of its vertices have degree $d$. We've seen that $G_q$ is $\frac{q-1}{2}$-regular.

9. Eigenvalues of a graph $G$ are the eigenvalues of its adjacency matrix $A_G$. 

10. Eigenvalues of a graph and its complement comes in pairs. More specifically, $k$-regular graph $G$ with $n$-vertices has $k$ being its eigenvalue. Let other $n-1$ eigenvalues be $\lambda_i$'s, then the eigenvalues of complement $\bar{G}$ of $G$ are $n-1-k$ and $-\lambda_i-1$'s.

Proof: Use linear algebra. Write $J$ matrix with $1$'s and $I$ the identity, the key here is to note $A_G + A_{\bar{G}}=J-I$.

11. A graph $G$ is $(n,d,\lambda,\mu)$-strongly regular if $X$ is $d$-regular with $n$-vertices, and any two adjacent vertices have $\lambda$ common neighbors and any non-adjacent vertices have $\mu$ common neighbors. A Paley graph is $(q,\frac{q-1}{2}, \frac{q-5}{4}, \frac{q-1}{4})$-strongly regular. 

12. The eigenvalues of $P_q$ are $\frac{q-1}{2}$ with multiplicity $1$ and $\frac{-1\pm\sqrt{q}}{2}$ each with multiplicity $\frac{q-1}{2}$.

@TODO: Understand [(page 15-16, and chapter 3, 4 for reviews on Representation theory and field extension)](https://open.library.ubc.ca/media/stream/pdf/24/1.0395514/3) Special cases of [characters in prime field](https://www.math.mcgill.ca/goren/GS/Reciprocity%20Laws.pdf). [Quatratic forms over finite fields](https://personal.math.ubc.ca/~cass/research/pdf/FiniteFields.pdf)
Proof: (Unfinished) Recall from representation theory that character of a representation $\rho:G\to GL(V)$ is a map $\chi_{\rho}:G\to F$ given by $g\mapsto Tr(\rho(g))$. Its degree is the dimension of the representation.


### A bit on random graph

Idea: Clique number of random subgraph of $P_q$ is **expected** to be much smaller than $O(\sqrt{q})$. It's $O(\log^2 q)$ using a general result for $(n,d,\lambda)$-expander graph, and there is an unpublished result giving an $O(\log q)$.


@TODO: Read pp.19-20

1. Write $G(n,\frac{1}{2})$ the graph of $n$ vertices and the probability of having an edge between any two edge being $\frac{1}{2}$.


### Improvement on the bound

@TODO: Read chapter 4-7 of Yep. 



### Breaking upper bound of $O(\sqrt{q})$?
**The above theoretical improvements fails to break $O(\sqrt{q})$.** How can we find $\epsilon>0$ small so that it's $O(q^{1/2-\epsilon})$?

1. Clique problem can be formulated as boolean optimization problem:

$$\omega(G) = \max_{y\in K_G} 
        \sum_{i\in V}y_i, \text{ where }K_G :=\{y\in\{0,1\}^V | y_iy_j = 0 \text{ if } \{i,j\}\not\in E\}.
$$
* Here $\{0,1\}^V$ is understood as a space of "guesses", and $K_G$ is understood as a space of "valid guesses". The boolean variables indicates which vertices are chosen. Element in $K_G$ are the vertices which form a clique in $G$.

This is a semidefinite programming problem since the constraint m