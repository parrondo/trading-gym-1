# Trading Gym for Quantitative trading

## Intro

This is a trading gym for any agent to trade for short term trading. We have enermous data for short term trading. We have been gathering for every Korean equities order and quote data every tick moment and also reflected data to our trading gym. **Trading Gym is a toolkit for developing and comparing reinforcement learning trading algorithms.**




## Basics

There are two basic concepts in reinforcement learning: the environment (namely, the outside world) and the agent (namely, the algorithm you are writing). The agent sends actions to the environment, and the environment replies with observations and rewards.

 **Trading Gym recreates market states based on trade orderbook and execution data. In this environment, you can make reinforcement learning agents learn how to trade.**

The core gym interface is [Env](https://github.com/openai/gym/blob/master/gym/core.py), which is the unified environment interface. There is no interface for agents; that part is left to you. The following are the `Env` methods you should know:

- reset(self): Reset the environment's state. Returns observation.
- step(self, action): Step the environment by one timestep. Returns observation, reward, done, info.
- render(self, mode='human', close=False): Render one frame of the environment. Display gym's status based on a user configurations.




## Architecture
It's is simple architecture that you motivate follow and run this repo easily.

![](/materials/architecture.png)


## How to install
You can clone two repository into your local computer or cloud whatever. And you can run agent after including traidng gym as submodule or add gym's root into Python Path and then you can run trading agent itself. so simple!



You can do install of trading gym simply with:

```
git clone https://github.com/6-Billionaires/trading-gym.git
```



## Quick Run

```
env = MyTGym(episode_type='0', percent_goal_profit=2, percent_stop_loss=5, episode_duration_min=60) # set env.

state = env.reset() # initiate env and get state

next_state, reward, done, info = env.step(action) # Do action and get next step information
```

An environment for learning reinforcement learning has been created, and reinforcement learning can be learned by designing agents.





## Data

You have to put trade orderbook and execution data into data folder. You must use the data in accordance with the format. The data format can be found in the 'data' folder on github.

Path : trading-gym\\data\\'Episode type'\\'Stock code'\\

- Episode type : Type what criteria you categorized your data
- Stock code : stock codes within certain episodes



Trade Orderbook Data Format

- File name format : 'Episode type'-'Stock code'-'Date'-order.csv
- It have 41 columns with time, bid prices (10), bid volumes (10), ask prices (10), ask volumes (10)



Trade Execution Data Format

- File name format : 'Episode type'-'Stock code'-'Date'-quote.csv
- It have 12 columns with time, price(last executed), Buy/Sell/Total executed, Buy/Sell/Total Weighted Price, Execution Strength, Open/High/Low Price







## Agent with this gym

[Here](https://github.com/6-Billionaires/trading-agent) can be reference. Those are that we built in temporary.




## Reference

### Other Gyms already built
1. Trading gym followed by OpenAI Gym architecture, spread trading
- https://github.com/Prediction-Machines/Trading-Gym

2. Trading gym followed by OpenAI Gym architecture, easy to look around with ipython example
- https://github.com/hackthemarket/gym-trading
- https://github.com/hackthemarket/gym-trading/blob/master/gym_trading/envs/TradingEnv.ipynb

3. Sairen
- Trading gym using API of Interative Broker  
- It is such a good reference for us. we will adapt live/paper mode feature of it.
    - https://doctorj.gitlab.io/sairen/
    - edemo / demouser
    * TWS configuration
        . TWS session will be set for socket port 7496 (live),
        . a paper account session will listen on socket port 7497 (paper)
        . https://interactivebrokers.github.io/tws-api/initial_setup.html#gsc.tab=0
4. deep trader
- [link](https://github.com/deependersingla/deep_trader)

### Reinforcement learning
[Algorithms collections based on OpenAI Gym](https://github.com/rll/rllab)
[best article](https://discuss.openai.com/t/gym-and-agent-for-algorithmic-stock-and-cryptocurrency-trading/519/23) to make trading gym on Discourse

### Plan

1. Packaging  
    [setup.py](https://www.digitalocean.com/community/tutorials/how-to-write-modules-in-python-3#accessing-modules-from-another-directory), [Upload package into pip repo ](https://stackoverflow.com/questions/15746675/how-to-write-a-python-module-package)
2. Refactoring
    [1](http://docs.python-guide.org/en/latest/writing/structure/), [2](https://jeffknupp.com/blog/2014/02/04/starting-a-python-project-the-right-way/)

3. Run this on cloud and allow every agent can access through REST API to train
