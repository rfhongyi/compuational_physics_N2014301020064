import pylab as pl
class uranium_decay:
    def __init__(self, number_of_nuclei_A = 100,\
    number_of_nuclei_B = 0,time_constant_1 = 2,\
    time_constant_2 = 1, time_of_duration = 8,\
    time_step = 0.05,time_step1 = 0.10,number_of_nuclei_A1 = 100,number_of_nuclei_B1 = 0):
        # unit of time is second
        self.n1_uranium = [number_of_nuclei_A ]
        self.n2_uranium = [number_of_nuclei_B ]
        self.n11_uranium = [number_of_nuclei_A1 ]
        self.n21_uranium = [number_of_nuclei_B1 ]
        self.t = [0]
        self.tau1 = time_constant_1
        self.tau2 = time_constant_2
        self.dt = time_step
        self.dt1 = time_step1
        self.time = time_of_duration
        self.nsteps = int(time_of_duration // time_step + 1)
        self.nsteps1 = int(time_of_duration // time_step1 + 1)
        print("Initial number of nuclei A ->", number_of_nuclei_A)
        print("Initial number of nuclei B ->", number_of_nuclei_B)
        print("Initial number of nuclei A ->", number_of_nuclei_A1)
        print("Initial number of nuclei B ->", number_of_nuclei_B1)
        print("Time constant A ->", time_constant_1)
        print("Time constant B ->", time_constant_2)
        print("time step -> ", time_step)
        print("time step -> ", time_step1)
        print("total time -> ", time_of_duration)
    def calculate(self):
        for i in range(self.nsteps):
            tmp1 = self.n1_uranium[i] - self.n1_uranium[i] /self.\
            tau1 * self.dt+self.n2_uranium[i] / self.tau2 * self.dt
            tmp2 = self.n2_uranium[i] - self.n2_uranium[i] /self.\
            tau2 *self.dt+self.n1_uranium[i] / self.tau1 * self.dt
            tmp11 = self.n11_uranium[i] - self.n11_uranium[i] /\
            self.tau1 * self.dt1+self.n21_uranium[i] /\
            self.tau2 * self.dt1
            tmp21 = self.n21_uranium[i] - self.n21_uranium[i] /\
            self.tau2 *self.dt1+self.n11_uranium[i] /\
            self.tau1 * self.dt1
            self.n1_uranium.append(tmp1)
            self.n2_uranium.append(tmp2)
            self.n11_uranium.append(tmp11)
            self.n21_uranium.append(tmp21)
            self.t.append(self.t[i] + self.dt)
    def show_results(self):
        pl.plot(self.t, self.n1_uranium)
        pl.plot(self.t, self.n2_uranium)
        pl.plot(self.t, self.n11_uranium)
        pl.plot(self.t, self.n21_uranium)
        pl.xlabel('time ($s$)')
        pl.ylabel('Number of Nuclei ')
        pl.legend(['$N_A$','$N_B$'])
        pl.show()
    def store_results(self):
        myfile = open('nuclei_decay_data.txt', 'w')
        for i in range(len(self.t)):
            print(self.t[i], self.n1_uranium[i], file = myfile)
            print(self.t[i], self.n2_uranium[i], file = myfile)
            print(self.t[i], self.n11_uranium[i], file = myfile)
            print(self.t[i], self.n21_uranium[i], file = myfile)
        myfile.close()
a = uranium_decay()
a.calculate()
a.show_results()
a.store_results()
