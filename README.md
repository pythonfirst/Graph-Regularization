# Graph-Regularization
MATLAB scripts for computing “Graphs Regularization Exploiting Data Trajectories On Temporal Manifolds”

G_start.m: initialize a structure with default (changeable) parameters

G_train.m: training the structure, data must be provide in a matrix containing row-wise the samples with relative targets (for classification tasks,binary target is assumed, prediction evaluated as the max between output)

G_test.m: evaluate the performance after training, assume a sequence with possible repetitions of data, then average performance w.r.t. the sequence (averaging on the repetitions of the same sample)

BuildingMatrix.m: compute the matrices of the prediction function dynamical system

PlotImpulsiveResponse.m: plot the Impulsive Response of the dynamical system

data_split.m: randomly select a percentage of supervisions from a dataset

random_walk.m: generate a random walk on a set of data

Data01.mat: contain the MNIST(*) sample for digits 0,1
(*) see: http://yann.lecun.com/exdb/mnist/

SequencesSeries01.mat: contains different sequence of different lengths generated by random_walk.m from Data01.mat useful for train the model

es:  
load('SequencesSeries01.mat');
load('Data01.mat');
G=G_start;
G=G_train(G,D01(ShTr01(1).S,:),1);
[~,Performance] = G_test(G,Test01,ShTe01(1).S,1);

MultipleTest.m: multiple test on all different lengths of train and test sequences in SequencesSeries01.mat and with different percentages of supervisions