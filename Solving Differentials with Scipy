# -*- coding: utf-8 -*-
import numpy as np
import pylab as py
from scipy.integrate import odeint

#LINK TO VPYTHON: http://www.glowscript.org/#/user/tmdahnou/folder/Public/program/OscillatingSprings/edit
def DE(s,t,p):
    Xa = s[0]
    Va = s[1]
    Xb = s[2]
    Vb = s[3]
    
    Ma=p[0]
    Mb=p[1]
    Kl=p[2]
    Km=p[3]
    Kr=p[4]
    
    Aa=-((Kl*Xa)+Km*(Xa-Xb))/Ma
    Ab=-((Kr*Xb)+Km*(Xb-Xa))/Mb
    
    deriv = [Va,Aa,Vb,Ab]
    return deriv


def diffeq_solver_from_scipy(s_initial, p, tmin, tmax, nts, deriv):
    t = np.linspace(tmin,tmax,nts)
    X = odeint(deriv, s_initial, t, args=(p,))
    
    return t,X
    
# Initial values
s_initial = [5.0,10.0,10.0,10.0]
p1 = [1, 1, 0.5, 1,1]
p2 = [1, 1000, 0.5, 1,1]
p3 = [1, 1, 0.5, 1,1]
tmin = 0
tmax = 20
nts = 200


(t,Xa) = diffeq_solver_from_scipy(s_initial, p1, tmin, tmax, nts, DE)
print Xa
(t,Xb) = diffeq_solver_from_scipy(s_initial, p2, tmin, tmax, nts, DE)
(t,Xc) = diffeq_solver_from_scipy(s_initial, p3, tmin, tmax, nts, DE)

# print Xa[:, 0]
# print Xa[:, 2]
#print
# print Xb[:, 0]
# print Xb[:, 2]
#print
# print Xc[:, 0]
# print Xc[:, 2]

py.figure(1)
py.plot(t,Xa[:,0], 'r', Label = '$x_1$')
py.plot(t,Xa[:,2], 'b', Label = '$x_2$')


py.title('First Conditions - Motion of Coupled Oscillator')
py.xlabel('Time (s)')
py.ylabel('$x(t)$')
py.legend()

py.figure(2)
py.plot(t,Xb[:,0], 'r', Label = '$x_1$')
py.plot(t,Xb[:,2], 'b', Label = '$x_2$')


py.title('Second Conditions - Motion of Coupled Oscillator')
py.xlabel('Time (s)')
py.ylabel('$x(t)$')
py.legend()


py.figure(3)
py.plot(t,Xc[:,0], 'r', Label = '$x_1$')
py.plot(t,Xc[:,2], 'b', Label = '$x_2$')

py.title('Third Conditions - Motion of Coupled Oscillator')
py.xlabel('Time (s)')
py.ylabel('$x(t)$')
py.legend()
py.show()

