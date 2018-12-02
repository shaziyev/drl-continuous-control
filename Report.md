
# Udacity DRL Navigation Project Report

### Algorithm Overview
The agent model is based on the Deep Deterministic Policy Gradients (DDPG) algorithm, which is based on the Actor-Critic networks. The Actor network is used to calculate the action based on the current state. The Critic network is used to predict the Q-value, i.e. the value of the current (state, action). The negative of the Q-value is used as a loss measure for training the Actor network. To measure the loss of the Critic network, a "true" or target Q-value is calculated using the Bellman equation, which in pseudocode looks like `Q_targets = rewards + gamma * critic_target(next_states, actions_next)`

The Actor network hyperparameters:
* Hidden layers: 2
* 1st hidden layer nodes (FC): 400
* 2nd hidden layer nodes (FC): 300
* Output layer nodes (actions): 4
* Input parameters (states): 33
* Activation function: ReLU (except output - tanh)

The Critic network hyperparameters:
* Hidden layers: 2
* 1st hidden layer nodes (FC): 400
* 2nd hidden layer nodes (FC): 300
* Output layer nodes (Q-value): 1
* Input parameters (states): 33
* Activation function: ReLU

### Training
The agent model was trained on Mac.
The following hyperparameters were used:
* Optimizer: Adam
* Replay buffer size: 100000
* Minibatch size: 64
* Discount factor (Gamma): 0.99
* Learning rate: 0.0005
* Epsilon (for epsilon-greedy action selection): starting with 1.0 and ending with 0.01 in 200 updates
* Network update rate (steps): 4

The agent was able to solve the environment (16+ scores) in 1098 episodes:

```
Episode 100	Average Score: 2.11
Episode 200	Average Score: 6.47
Episode 300	Average Score: 9.14
Episode 400	Average Score: 10.71
Episode 500	Average Score: 12.96
Episode 600	Average Score: 13.46
Episode 700	Average Score: 14.51
Episode 800	Average Score: 14.89
Episode 900	Average Score: 15.50
Episode 1000	Average Score: 15.17
Episode 1100	Average Score: 15.71
Episode 1198	Average Score: 16.01
Environment solved in 1098 episodes!	Average Score: 16.01
```

![Rewards Plot](attachment:image.png)

### Future Ideas
It would be great to compare performance of Double DQN (DDQN), Dueling DQN, Prioritized DQN, Noisy DQN and finally Rainbow
