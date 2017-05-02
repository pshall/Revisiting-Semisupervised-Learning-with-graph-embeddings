# Revisiting-Semisupervised-Learning-with-graph-embeddings

                      Revisited semisupervised learning with graph embeddings 


Libraries Used :lasagne,Theano,numpy 

1. Instructions for setting up and running the code: 
Run following file: 
python test_trans.py 


2. Structure of the code : 
The implementation is divided into 4 files: 
1. test_trans.py 
It is driver program that starts our model implementation and starts iteration.It loads the specific dataset using pickles along with the test and train files.It calls the function which are available in trans_model.py to train model. 

2. trans_model.py 
this file contains function that generates graph along with their embeddings.It also predicts the label of the graph along with its context. 

3. base_model.py 
this files contains various funtions that loads ans stores paramenter,computer iterations and train model 

4. layers.py 
this is the heart of the model.it contains neural network functions that we apply during training.several layers are there including dense-layer,sparse-layer,softmax_layer etc. 


3. Important points regarding the codebase 
The model is implemented mainly in trans_model.py , with inheritance from base_model.py. 

We start with loading dataset in a form of list and then make tuple from that list.Then we start training of our model with some fix number of iteration labels and graph.We already fixed value of max accuracy so for some fixed number of iteration if we find accuracy greater then maximum accuracy then we are storing the parameter into some data structure for that accuracy. 

While iterating we are generating graph. 

Layers are used in neural network to predict label and context for the embedding of the graphs. 
Finally we are displaying following result during training:
* instance number along with loss in label generation 
* graph instance numebr along with loss in context generation 
* ieration count and accuracy along with maximum accuracy. 

Input to the model: 
The input to the transductive model contains: 
* x, the feature vectors of the training instances, 
* y, the one-hot labels of the training instances, 
* graph, a dict in the format {index: [index_of_neighbor_nodes]}, where the neighbor nodes are organized as a list. The current  version only supports binary graphs. 

Let L be the number of training instances. The indices in graph from 0 to L - 1 must correspond to the training instances, with the same order as in x. 
Preprocessed dataset
Datasets for Cora is available in the directory data, in a preprocessed format stored as numpy/scipy files.

In addition to x,y, and graph as described above, the preprocessed datasets also include: 
*  tx, the feature vectors of the test instances, 
*  ty, the one-hot labels of the test instances, 
*  test.index, the indices of test instances in graph, for the inductive setting, 
*  ally, the labels for instances in allx 
*  allx, list of all instances 

The indices of test instances in graph for the transductive setting are from “#x” to “#x + #tx – 1”,
with the same order as in “tx”.

4. Hyper-perameter tuning: 
Hyper-parameters are tuned by randomly shuffle the training/test split (i.e., randomly shuffling the indices in "x", "y", "tx", "ty", and "graph").We tune the hyper-parameters on one of the ten runs, and then keep the same hyper-parameters for all the ten runs. 


5. Results are added as screenshots in result subfolder.
   Accuracy : We are getting  0.63-0.67  which is slightly less than stated in paper.
