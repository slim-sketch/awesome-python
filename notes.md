#Python学习笔记（经管数据分析）
##用到的库
1.numpy：数据计算
2.pandas：表格数据处理
3.matplotlib：基础绘图，画PPF，饼图，供需曲线
4.seaborn：统计可视化，回归图，热力图
5.scikit—learn：机器学习模型（回归，分类，聚类）

# Python学习笔记｜Sklearn 线性模型 Linear Models
> 文档来源：scikit-learn official docs
## 基础公式
预测值：
$\hat y = w_0 + w_1x_1 + w_2x_2 + ... + w_px_p$
- $\hat y$：模型预测值
- $x_1,x_2...$：特征/自变量（经济学：价格、收入等）
- $w_1,w_2...$：coef_ 系数，代表自变量边际影响
- $w_0$：intercept_ 截距

## 1.1.1 Ordinary Least Squares（OLS普通最小二乘）
对应代码：LinearRegression
目标：最小化残差平方和，找到一条离所有样本点最近的拟合直线。经管实证、供需曲线建模首选。

## 右侧目录术语
1. Classification：线性模型做分类任务，代表算法：LogisticRegression逻辑回归（预测类别，不是数字）
2. Ridge complexity：岭回归，增加正则惩罚，控制模型复杂度，缓解多重共线性问题
3. regularization parameter：正则化参数alpha，alpha越大，惩罚力度越强，用来防止过拟合
4. leave-one-out Cross Validation（LOOCV留一法交叉验证）
每次拿1条数据做测试，其余训练；循环全部样本，用来挑选最优alpha，适合小样本经济学数据
5. Lasso 拉索回归：带正则，可以直接把不重要变量的系数压缩到0，自动筛选变量
> Ridge只缩小系数；Lasso能直接剔除无关变量
6. Least angle regression(LAR) 最小角回归：Lasso底层求解算法，日常调用Lasso不用手动操作

## 简单对比
OLS：无惩罚，简单可解释，但容易多重共线性、过拟合
Ridge：压缩系数，保留全部变量
Lasso：压缩系数，自动剔除不重要变量
