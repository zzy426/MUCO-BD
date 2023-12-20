# MUCO-BD
论文《基于多模态对比学习的输电线路螺栓缺陷分类》中的预训练模型，代码将在后续开源...

预训练模型：https://pan.baidu.com/s/1SDJlxAwTpgXsJGAHJVYRGw?pwd=6382

提取码: 6382

所需依赖包和基本API（加载权重除外）可参考Chinese-CLIP：https://github.com/OFA-Sys/Chinese-CLIP

使用方法：

# 加载完整模型：
device = torch.device("cuda:0" if torch.cuda.is_available() else "cpu")
model, preprocess = load_from_name("ViT-B-16", device=device, download_root='./pretrained_weight/cn-clip') #加载原始CN-CLIP-vit
model.load_state_dict(torch.load('./MUCO-BD-vit.pth')) #把权重替换为上述链接中的预训练权重

# 提取图像/文本编码器：
image_encoder=model.visual
text_encoder=model.bert

# 添加线性分类头构建图像分类模型（文本提示分类头后续开源）:
image_classifier = nn.Sequential(
    image_encoder,
    nn.Linear(in_features=512, out_features=num_classes, bias=True)
)

-----------------------------------------------------------------------------------------------------------------------------------------------------------------

The pretrained models of &lt;Transmission Line Bolt Defects Classification Based on Multi-Modal Contrastive Learning>, and the code will be released later...

pretrained models: https://pan.baidu.com/s/1SDJlxAwTpgXsJGAHJVYRGw?pwd=6382

extract code: 6382

the required packages and APIs (loading weights excepted) can refer to Chinese-CLIP: https://github.com/OFA-Sys/Chinese-CLIP

usage:

# load the full model:
device = torch.device("cuda:0" if torch.cuda.is_available() else "cpu")
model, preprocess = load_from_name("ViT-B-16", device=device, download_root='./pretrained_weight/cn-clip') #load original CN-CLIP-vit
model.load_state_dict(torch.load('./MUCO-BD-vit.pth')) #replace the weights with the pre-trained weights from above link

# extract the image/text encoder:
image_encoder=model.visual
text_encoder=model.bert

# add linear classification head to construct an image classifier (classification heads based on text prompt will be released later)
image_classifier = nn.Sequential(
    image_encoder,
    nn.Linear(in_features=512, out_features=num_classes, bias=True)
)
