**Rank-1 Constraint Systems** #R1CS (In-Progress)

Rank-1 Constraint systems refer to a system of linear-equations of the form $Az*Bz=Cz$ where $A,B,C$ are matrices with dimensions $n*m$ where 

$n=$ number of constraints
$m =$ number of witness variables

## Example

Instead of starting with a basic example like $x =y*z$ , we start with a more advanced example.

$$
z = x^2*y + 3*x + 2

$$

We choose this examples to help the reader grasp the following important concepts about the R1CS representation 
- Addition of a witness variable with constant is free in R1CS. 
- Multiplication of a witness variable with a constant (or in other words scaling a witness variable linearly) is free in R1CS

Note: **Free** simply means we don't need additional constraints (Additional rows in our matrices $A,B,C$ to encode relations like addition and multiplication with a constant of a witness variable.)
In SNARK proof systems, the cost to the prover is almost always linear in the number of constraints, so more constraints = more work for the prover. 

$z = x^2*y + 3*x + 2$

Let us shift some terms around, we shall see how this helps us later on 
$z - 3*x = x^2*y$

Now lets calculate the intermediate representations, An R1CS representation only allows us to multiply two variables in the witness vector at once. 
$v_{1}=x^2$
$z - 3*x = v_1*y$

It is now time to state what our witness vector is. The witness vector $w$ contains all the intermediate variables, the public input-output and the private variables
$\mathbf{w} = [ \vec{1,v_1,z,x,y} ]$ 

Here are out corresponding $A,B,C$ matrices. 

$$A = 
\begin{vmatrix}
0 & 0 & 0 & 1 & 0 \\
0 & 1 & 0 & 0 & 0 \\
\end{vmatrix}
\\ , 
B = \begin{vmatrix}
0&0&0&1&0 \\ 
0&0&0&0&1
\end{vmatrix}
\\ , 
C = 
\begin{vmatrix}
 0 & 1 & 0 & 0 & 0                 \\
0 & 1 & 0 & -3 & 0 
\end{vmatrix}
$$
